# TCP 

**TCP (Transmission Control Protocol)** 和 **UDP (User Datagram Protocol)** 都是传输层的协议，用于数据传输。

1. **可靠性**: 
   - **TCP**：是可靠的，确保数据完整性和顺序。
   - **UDP**：是不可靠的，没有错误检查机制。

2. **连接**:
   - **TCP**：是面向连接的，需要建立连接后才能传输。
   - **UDP**：是无连接的，直接发送数据。

3. **速度**:
   - **TCP**：相对较慢，因为它确保数据的可靠性。
   - **UDP**：速度快，因为没有复杂的错误检查。

4. **用途**:
   - **TCP**：常用于需要高可靠性的服务，如Web服务器、邮件服务器等。
   - **UDP**：常用于快速传输和实时服务，如视频、语音通话等。

5. **头部信息**:
   - **TCP**：头部信息量较大。
   - **UDP**：头部信息量较小。

6. **流控和拥塞控制**:
   - **TCP**：有流控和拥塞控制机制。
   - **UDP**：没有这些机制。

## 🚚 快递员与飞鸽传书：TCP vs UDP

<div align=center><img src="img/20231011165105.png" width="60%"></div>

想象你有两种方式来传递消息：

1. **快递员 (TCP)** 📦：  
   - 他会敲门确保你在家，然后才交给你包裹。
   - 如果你不在，他会再次尝试直到成功交付。
   - 快递员确保包裹的顺序正确，即使他需要花更多时间。
   - _这就像TCP的可靠性，面向连接性和确保数据的完整性及顺序。_

2. **飞鸽 (UDP)** 🐦：
   - 它只是飞过并扔下消息，不会确认你是否收到。
   - 飞鸽很快，因为它不等待任何确认。
   - 有时，飞鸽可能会掉落或错放消息。
   - _这就像UDP的速度和不可靠性，它不需要建立连接就可以直接发送数据。_

**其他区别**:
   - 要给快递员的费用可能会更高，因为他提供了更多的服务和确认。（_TCP的头部信息量较大_）
   - 飞鸽只需要足够的食物来飞行并投递消息。（_UDP的头部信息量较小_）
   - 快递员可能会因为道路拥堵而推迟交付，但他总会找到最佳路径。（_TCP的流控和拥塞控制_）
   - 飞鸽不考虑其他飞鸽或空中的障碍，它只是直接飞行。（_UDP没有这些机制_）