# I2C

## I2C简介

**IIC**：Inter Integrated Circuit，集成电路总线，一种同步、半双工通信总线
![](assets\Snipaste_2024-01-30_18-09-47.png)
 <center> I2C总线物理拓扑图 </center>

## I2C物理层
- SDA：数据线
- SCL：时钟线
- 允许多主机存在，I2C总线上的每个设备都自己一个唯一的地址

## I2C协议层
- 开始信号：SCL 为高电平时，SDA 由高电平向低电平跳变，开始传送数据。
- 结束信号：SCL 为高电平时，SDA 由低电平向高电平跳变，结束传送数据。
- 应答信号：接收数据的 IC 在接收到 8bit 数据后，向发送数据的 IC 发出特定的低电平脉冲，表示已收到数据。（低电平 0 表示应答，高电平 1 表示非应答）
- 数据有效性：IIC 信号在数据传输过程中，当 SCL=1 高电平时，数据线 SDA 必须保持稳定状态，不允许有电平跳变，只有在时钟线上的信号为低电平期间，数据线上的高电平或低电平状态才允许变化。
![](assets\Snipaste_2024-01-30_18-24-41.png)
**注意**：空闲状态下，SCL 和 SDA 均处于高电平。

## I2C数据传输
- I2C写入数据
    ![](assets\Snipaste_2024-01-30_19-22-12.png)
    - 主机首先产生START信号
    - 然后紧跟着发送一个从机地址，这个地址共有7位，紧接着的第8位是数据方向位(R/W)，0表示主机发送数据(写)，1表示主机接收数据(读)
    - 主机发送地址时，总线上的每个从机都将这7位地址码与自己的地址进行比较，若相同，则认为自己正在被主机寻址，根据R/T位将自己确定为发送器或接收器
    - 这时候主机等待从机的应答信号(A)
    - 当主机收到应答信号时，发送要访问从机的那个地址，继续等待从机的应答信号
    - 当主机收到应答信号时，发送N个字节的数据，继续等待从机的N次应答信号
    - 主机产生停止信号，结束传送过程

- I2C读取数据
    ![](assets\Snipaste_2024-01-30_19-22-41.png)
    - 主机首先产生START信号
    - 然后紧跟着发送一个从机地址，注意此时该地址的第8位为0，表明是向从机写命令
    - 这时候主机等待从机的应答信号(ACK)
    - 当主机收到应答信号时，发送要访问的地址，继续等待从机的应答信号
    - 当主机收到应答信号后，主机要改变通信模式(主机将由发送变为接收，从机将由接收变为发送)所以主机重新发送一个开始start信号，然后紧跟着发送一个从机地址，注意此时该地址的第8位为1，表明将主机设置成接收模式开始读取数据
    - 这时候主机等待从机的应答信号，当主机收到应答信号时，就可以接收1个字节的数据，当接收完成后，主机发送非应答信号，表示不再接收数据
    - 主机进而产生停止信号，结束传送过程

## I2C相关HAL库驱动

- I2C初始化
  ![](assets\Snipaste_2024-01-30_20-08-47.png)
- I2C传输数据
  ```c
  // 发送数据
  HAL_StatusTypeDef HAL_I2C_Master_Transmit(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size, uint32_t Timeout)

  // 接收数据
  HAL_StatusTypeDef HAL_I2C_Master_Receive(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint8_t *pData, uint16_t Size, uint32_t Timeout)

  //上述均为阻塞模式，后续补充中断和DMA模式
  ```
- I2C内存访问
  ```c
  // 内存写入
  HAL_StatusTypeDef HAL_I2C_Mem_Write(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint16_t MemAddress, uint16_t MemAddSize, uint8_t *pData, uint16_t Size, uint32_t Timeout)

  // 内存读取
  HAL_StatusTypeDef HAL_I2C_Mem_Read(I2C_HandleTypeDef *hi2c, uint16_t DevAddress, uint16_t MemAddress, uint16_t MemAddSize, uint8_t *pData, uint16_t Size, uint32_t Timeout)
  ```
- I2C回调函数
  ```c
  // 接收完成回调
  void HAL_I2C_MasterRxCpltCallback(I2C_HandleTypeDef *hi2c)

  // 内存访问回调
  void HAL_I2C_MemRxCpltCallback(I2C_HandleTypeDef *hi2c)
  ```