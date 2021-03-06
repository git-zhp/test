# [**进口二级库手持系统需求说明书**]() {#u5K9e}

**修订记录**

| 修订人 | 修订时间 | 修订内容 | 备注 | 版本号 |
| :--- | :--- | :--- | :--- | :--- |
| 陈虎 | 20191201 | 首次编写 | - | V1.0 |
| 陈虎 | 20191206 | 增加需求列表、对编写范围进行调整； | - | V1.1 |
| 陈虎 | 20191210 | 增加手持客户端升级以及IWS增加版本管理 | - | V1.2 |
| 陈虎 | 20191216 | 增加项目概述；部分页面字段说明；新增详细流程介绍；增加电子签章方案；出库流程微调（确认出库只能整个出库单整体确认出库）；IWS往来单位信息管理增加客户邮箱地址维护； | - | V1.3 |
| 陈虎 | 20191218 | 理货模块（创建理货/分单详情）增加字段：IPPC； | - | V1.4 |
| 陈虎 | 20191219 | 理货模块（创建理货/分单详情）增加字段：存放温度、包库；增加入库模块邮件发送的校验规则以及发送前的备注填写； | - | V1.5 |























































[进口二级库手持系统需求说明书1]()

[1.项目概述5]()

[1.1.愿景5]()

[1.2.总体目标5]()

[1.2.1.手持系统5]()

[1.2.2.出库流程优化6]()

[1.2.3.实施目标6]()

[2.总体流程7]()

[2.1.入库流程7]()

[2.1.1.业务模型7]()

[2.1.2.流程设计8]()

[2.2.出库流程8]()

[2.2.1.业务模型8]()

[2.2.2.流程设计9]()

[3.需求列表9]()

[3.1.手持客户端9]()

[3.2.预约提货端（H5）10]()

[3.3.IWS改造11]()

[3.4.提货报到端（H5）11]()

[4.详细设计11]()

[4.1.功能设计11]()

[4.1.1.手持客户端11]()

[4.1.1.1.启动页11]()

[4.1.1.2.版本更新12]()

[4.1.1.3.登录14]()

[4.1.1.4.首页16]()

[4.1.1.5.理货18]()

[4.1.1.5.1.理货列表/搜索列表18]()

[4.1.1.5.2.创建理货22]()

[4.1.1.5.3.搜索27]()

[4.1.1.5.4.分单详情29]()

[4.1.1.6.入库32]()

[4.1.1.6.1.入库列表32]()

[4.1.1.6.2.搜索36]()

[4.1.1.6.3.分单详情37]()

[4.1.1.7.盘点39]()

[4.1.1.7.1.盘点列表39]()

[4.1.1.7.2.盘点详情42]()

[4.1.1.8.出库47]()

[4.1.1.8.1.出库单认领47]()

[4.1.1.8.1.1.认领列表47]()

[4.1.1.8.1.2.认领详情49]()

[4.1.1.8.2.我的出库单51]()

[4.1.1.8.2.1.我的出库单列表51]()

[4.1.1.8.2.2.未出库详情53]()

[4.1.1.8.2.3.已出库详情56]()

[4.1.2.预约提货（H5）58]()

[4.1.3.IWS改造61]()

[4.1.3.1.手持盘点61]()

[4.1.3.1.1.盘点单61]()

[4.1.3.1.1.1.盘点详情62]()

[4.1.3.2.提货预约65]()

[4.1.3.3.出库管理66]()

[4.1.3.4.电子签章68]()

[4.1.3.5.设备相关参数68]()

[4.1.3.6.具体交互68]()

[4.1.3.7.版本管理71]()

[4.1.3.7.1.版本列表71]()

[4.1.3.7.2.新增73]()

[4.1.3.7.3.编辑74]()

[4.1.3.7.4.查看75]()

[4.1.3.8.往来单位信息管理76]()

[4.1.4.提货报到（H5）77]()

[5.备忘录79]()

[5.1.邮件模板79]()

[5.2.入库单80]()







































































# **1.**[**项目概述**]() {#MyC1i}

## **1.1.愿景** {#rMrUB}

本项目依托宏远集团现有的业务以及现有的IWS平台，搭建手持系统，实现客户端手持理货、手持入库、手持盘点以及手持出库；同时完善现有的IWS出库流程，提升客户提货体验；

## **1.2.总体目标** {#nMBPu}

### **1.2.1.手持系统** {#sVi5N}

需要搭建一套完善的平台，支撑内部实操人员通过手机APP（安卓）实现理货、入库、盘点以及出库功能。

其中，IWS已经存在入库、盘点以及出库等功能模块，手持系统的业务数据中理货、入库需要本项目存储，在手持客户端确认入库时统一推送给IWS，需要在IWS内的入库管理模块中进行展示；

盘点、出库的数据均通过接口从IWS初始化获取，在手持客户端完成盘点以及出库操作；其中，盘点后的数据不需要直接对接IWS已存在的盘点模块，需要在IWS内建立新的盘点数据存储以及独立的数据结果展示；出库的数据直接对接IWS，在IWS的出库管理模块中展示；

### **1.2.2.出库流程优化** {#6y9jy}

IWS已经实现出库单的创建、打印以及出库功能，需要在此基础上实现出库单创建前的提货预约（扫码访问）、创建时的提货人员信息复用、打印前的电子签章、打印后的扫码提货报到功能；

### **1.2.3.实施目标** {#sRj9u}

本期项目需要覆盖以下内容：

**1个手持系统客户端项目**

实现理货、入库数据的存储，支撑手持入库、盘点、入库功能并同步给IWS；涉及用户客户端登录以及获取用户信息/库区信息/字典数据/盘点单信息/出库单等信息均从IWS接口实时获取，不另做存储；

**2个用户端**

预约提货端以及提货报到端，均通过扫码手机浏览器直接访问；

**IWS改造**

在原有的IWS管理后台增加：1、手持客户端版本管理；2、手持盘点模块3、提货预约信息查看4、出库单创建时的提货人信息复用5、电子签章、历史签章查阅6、出库单打印时增加出库单二维码7、出库单状态改造；

# **2.**[**总体流程**]() {#SJcRY}

## **2.1.**[**入库流程**]() {#syiMX}

### **2.1.1.业务模型** {#7o88J}

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739850273-7ab50110-8ae6-4dd7-b493-76d4602853ee.png "image")

### **2.1.2.**[**流程设计**]() {#du4LS}

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739850524-7b45fbc6-fdf1-453d-80cf-0de617782b2b.png "image")

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739850644-016d1a8b-2e85-435c-aab6-0c1fc9ec5b1a.png "image")

## ** ** {#sFuwi}

# **3.需求列表** {#1FdMS}

## **3.1.**[**手持客户端**]() {#Ek9uD}

| **模块** | **一级菜单** | **二级菜单** | **功能点** |
| :--- | :--- | :--- | :--- |
| 版本升级 | 版本更新提醒 |  | 版本更新 |
| 登录 |  |  | 登录 |
|  |  |  | 记住密码 |
|  |  |  | 启动页 |
| 首页 | 库区权限 |  | 库区权限获取查看 |
|  | 用户信息 |  | 用户名查看 |
|  | 退出登录 |  | 退出登录 |
|  | 理货 |  | 权限获取 |
|  | 入库 |  | 权限获取 |
|  | 盘点 |  | 权限获取 |
|  | 出库 |  | 权限获取 |
| 理货 | 理货列表 | 主单信息 | 主单信息显示 |
|  |  |  | 发送邮件 |
|  |  |  | 主单信息切换 |
|  |  | 分单列表 | 分单统计 |
|  |  |  | 分单信息显示 |
|  | 搜索 | 搜索 | 搜索 |
|  |  |  | 搜索列表 |
|  | 创建理货/分单详情/添加分单 | 创建理货/分单详情/添加分单 | 添加主单 |
|  |  |  | 添加分单 |
|  |  |  | 存放区域维护 |
| 入库 | 入库列表 | 主单信息 | 主单信息显示 |
|  |  |  | 邮件回复时间完善 |
|  |  |  | 发送邮件 |
|  |  |  | 主单信息切换 |
|  |  | 分单列表 | 分单统计 |
|  |  |  | 分单信息显示 |
|  | 搜索 | 搜索 | 搜索 |
|  |  |  | 搜索列表 |
|  | 分单详情 |  | 货位信息维护 |
|  | 确认入库 |  | 入库校验 |
|  |  |  | 入库单同步 |
| 盘点 | 盘点列表 |  | 状态筛选 |
|  |  |  | 盘点单查询 |
|  | 盘点 | 货位号列表 | 货位信息展示 |
|  |  | 货位号搜索 | 搜索 |
|  |  | 运单信息 | 运单信息维护 |
|  |  |  | 添加运单 |
|  |  |  | 暂存 |
|  |  |  | 盘点推送 |
| 出库 | 出库单认领 | 出库单列表 | 状态筛选 |
|  |  |  | 查看详情 |
|  |  |  | 认领 |
|  | 我的出库单 | 出库单列表 | 状态筛选 |
|  |  |  | 查看详情 |
|  |  |  | 退单 |
|  |  |  | 出库操作 |



# **4.**[**详细设计**]() {#o0W2D}

## **4.1.**[**功能设计**]() {#ODKM4}

### **4.1.1.**[**手持客户端**]()  {#4lb7M}

#### **4.1.1.5.理货** {#lJKiA}

##### **4.1.1.5.1.理货列表/搜索列表** {#YqSoD}

Ø原型设计

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739852614-2bf15467-baf2-4c2b-9136-1d176a477ee3.png "image")

Ø字段说明

| 元素名称 | 是否输入-类型 | 类型长度 | 是否必填 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| 主运单号 | N-仅显 | - | - | - |
| 客户代码 | N-仅显 | - | - | - |
| 品类 | N-仅显 | - | - | 根据主单号从IWS获取不到该字段信息，则显示“-” |
| 主单件数 | N-仅显 | - | - | 根据主单号从IWS获取不到该字段信息，则显示“-” |
| 理货件数 | N-仅显 | - | - | 分单列表中的理货件数之和，无则显示“-” |
| 分单总票数 | N-仅显 | - | - | 统计理货未完成、待入库、已入库状态的分单个数（重复的不累计统计）； |
| 分票总件数 | N-仅显 | - | - | 统计理货未完成、待入库、已入库状态的分单件数（重复的不累计统计）；若分单件数从IWS获取不到，则显示‘-’，不纳入统计； |
| 理货件数 | N-仅显 | - | - | 统计列表内待入库以及已入库的分单的总存放件数；没有待入库或已入库的分单，则显示“-”； |
| 分单号 | N-仅显 | - | - | - |
| 状态 | N-仅显 | - | - | 显示：理货未完成、待入库、已入库；已传输IWS状态下，该列表不展示； |
| 品类 | N-仅显 | - | - | 根据主单号+分单号从IWS获取不到该字段信息，则显示“-” |
| 分单件数 | N-仅显 | - | - | 根据主单号+分单号从IWS获取不到该字段信息，则显示“-” |
| 理货件数 | N-仅显 | - | - | 统计待入库以及已入库的分单的总存放件数；没有待入库或已入库的分单，则显示“-”； |



Ø功能描述

\(1\)点击![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739852714-d28c7bf6-d5f8-4bce-864c-9187b271e390.png "image")返回首页；

\(2\)点击![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739852771-9502abcd-551a-4bb1-a2f7-605b2b708399.png "image")进入搜索页；

\(3\)支持左右滑动查看上一或下一主单，若不存在上一/下一主单信息，滑动时提示“没有更多数据！”

\(4\)空态，保留顶部，页面显示“暂无数据！”；

**主单信息**

\(1\)展示最近添加且存在理货未完成或待入库或已入库的主单，若是搜索进入该页面，则展示复核搜索条件的最近添加且存在理货未完成或待入库或已入库的主单；

\(2\)显示主单号全部内容、客户代码、品类（空，显示：-）、分单（空，显示：-）件数、理货件数（空，显示：-，理货件数=分单列表中的理货件数之和）；

\(3\)预加载第二条主单信息；显示当前主单的顺序以及总数；![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739852842-909a21a8-86ee-42b1-8cd6-bcc7ff2c9ee7.png "image")

\(4\)发送邮件，若当前分单状态均为“理货未完成”，则提示“请先确认理货完成！”，若当前分单存在“待入库”或“已入库”时，点击时，弹框强提示：![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739852919-e47489a3-6bc2-4bea-ae45-06952ef5763e.png "image")点击取消，则弹框消失；点击确认，则向客户邮箱发送邮件；发送中弹框弱提示“发送中”，发送成功显示“发送成功！”发送失败，弱提示“发送失败，请稍后重试！”；

**分单信息**

\(1\)支持该列表下拉刷新；

\(2\)展示当前主单下的所有分单信息；

\(3\)分单总票数：显示列表内过滤相同分单号的分单数量；分票总件数：列表内的分票总件数，同一个分单不需要重复叠加；理货总件数：统计待入库以及已入库的分单的总存放件数；

\(4\)分单号：显示全部的分单号内容，一行显示不下的...代替；显示该记录的状态：理货未完成、待入库、已入库；品类、分单件数：显示全部内容，一行显示不下的...代替，没有内容的显示-；理货件数：理货未完成状态，显示-，待入库/已入库，统计该记录的存放件数之和；

\(5\)点击列表当前记录的整行区域，进入分单详情；

\(6\)按钮：创建理货、理货完成，按钮底部悬浮；点击创建理货进入创建理货页；

\(7\)理货完成：当前记录状态存在理货未完成状态时，该按钮可点击状态；若不存在理货未完成状态时，该按钮置灰不可点击；

**确认理货完成后：**

\(1\)理货未完成的记录将状态变更为待入库；其他状态不变更；

\(2\)确认理货完成，判断：A、当前主单下无未传输至IWS的入库单，当次理货完成时候，生成新的入库单；B、当前主单已存在未传输至IWS的入库单，当次理货完成的不分批的分单记录需要更新到首张已存在未传输至IWS的入库单内，当次理货完成的分批的分单记录需要生成新的入库单；

##### ** ** {#kBDmN}

### **4.1.3.**[**IWS改造**]()  {#T8K78}

#### **4.1.3.4.电子签章** {#DZySM}

##### **4.1.3.5.设备相关参数** {#Z3fd4}

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739859528-02d27507-305e-4805-b75c-69f6e2c96404.png "image")

具体参数见文档：![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739859667-49813a67-6356-46ec-b48c-7d8168154d26.png "image")

与手写设备对接过程中，字体大小、签字颜色、线条粗细，均按照接口规范中的默认值；

##### **4.1.3.6.具体交互** {#bhhCC}

**1\)签章触发**

在【代操作库管理】-【出库管理（代操作）】以及【公共服务区管理】-【出库管理（公共）】下操作出库办理-出库创建-点击电子签章：

检测硬件状态：

未检测到硬件（提示“未检测到硬件，请稍后重试！”）；

已检测到硬件：已签章（提示“该出库单已签章，请勿重复签章！”）、未签章（传输硬件展示内容，详情见下方【内容投放】）

**2\)内容投放**

Ø原型设计

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739860022-d6bd42b8-7000-41eb-81f7-f8da6bcec84a.png "image")

Ø字段说明

| 元素名称 | 是否输入-类型 | 类型长度 | 是否必填 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| 日期 | N-仅显 | - | - | 当前页面打开的日期 |
| 二维码 | N-仅显 | - | - | 通过二维码进入扫码报到（H5）页，并将出库单信息获取展示； |
| 出库单号 | N-仅显 | - | - | 英文字母需要大写，展示全部内容； |
| 客户代码 | N-仅显 | - | - | 英文字母需要大写，展示全部内容； |
| 出库时间 | N-仅显 | - | - | 出库单创建时间；格式：0000-00-0000:00:00 |
| 实际出库时间 | N-仅显 | - | - | 手持统一确认出库时间；格式：0000-00-0000:00:00，在签章时为空； |
| 主运单号 | N-仅显 | - | - | 不同主运单号分列显示； |
| 分运单号 | N-仅显 | - | - | 不同分运单号分列显示； |
| 存放区域 | N-仅显 | - | - | 相同主单-分运单号下不同存放区域分列显示； |
| 存放件数 | N-仅显 | - | - | 统计该主单-分单下的存放区域的存放计数； |
| 存放计量 | N-仅显 | - | - | 统计该主单-分单下的存放区域的存放计量； |
| 货位号 | N-仅显 | - | - | 统计该主单-分单下的存放区域的存放货位号，展示全部的货位号，允许换行；货位号间用“，”隔开 |
| 包装 | N-仅显 | - | - | 统计该主单-分单下的存放区域的包装信息，展示全部的包装信息，允许换行；多个包装信息间用“，”隔开 |
| 破损记录 | N-仅显 | - | - | 展示：有、无； |
| 加班 | N-仅显 | - | - | 展示：是（需要加班）、否（不需要加班）； |
| 提货公司名称 | N-仅显 | - | - | 提货单创建时的公司名称，没有则显示空； |
| 提货人姓名 | N-仅显 | - | - | 提货单创建时的提货人姓名，没有则显示空； |
| 联系方式 | N-仅显 | - | - | 提货单创建时的联系方式，没有则显示空； |
| 提货人签名 | N-仅显 | - | - | 未签章状态下为空，已签章状态下显示签章的图片； |
| 出库操作人员 | N-仅显 | - | - | 创建出库单的用户姓名； |



Ø功能描述

\(1\)点击签章，未签章状态下，将以上内容投放至签章设备；

\(2\)签章设备签字后，需要将整个PDF（内含提货人签字）保存至IWS；如图：

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739860156-a3b2ba1a-5516-4883-99f0-96fd9c68fb6a.png "image")

**3\)确认并打印**

点击确认并打印，若已签章，则将签章之后保存到系统内的PDF文件进行打印，若还未签章，则显示原有的打印页面，打印单中自动生成二维码（位置在左上角），通过扫描自动获取该出库单信息并手机浏览器直接访问“提货报到（H5）”页面；

#### **4.1.3.7.**[**版本管理**]() {#Pnxm1}

##### **4.1.3.7.1.版本列表** {#egEsp}

Ø原型设计

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739861113-16c0f425-d6c1-4eb5-a2df-ae9d427ea611.png "image")

Ø字段说明

| 元素名称 | 是否输入-类型 | 类型长度 | 是否必填 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
|  |  |  |  | 查询条件 |
| 是否强制更新 | Y-下拉单选 | - | - | 展示：不限、是、否；默认展示不限； |
| 添加时间 | Y-日期控件 | - | - | 默认为空，即查询所有数据； |
|  |  |  |  | 列表输出 |
| 版本号 | N-仅显 | - | - | - |
| 更新内容 | N-仅显 | - | - | 一行显示不下的直接省略号代替； |
| 是否强制更新 | N-仅显 | - | - | 展示：是、否 |
| 生成时间 | N-仅显 | - | - | 示例：0000-00-0000:00:00 |



Ø功能描述

\(1\)列表根据生成时间倒序排序；

\(2\)列表显示版本号、更新内容、是否强制更新一集生成时间，更新内容若一行显示不下，则...代替；

\(3\)提供查询条件“是否强制更新”、添加时间，“是否强制更新”默认：不限，可选择是或否，添加时间可以选择一个周期内，默认是选择某一个日期的0点0分0秒至某一个日期的23点59分59秒；

\(4\)列表需要进行数据分页展示；

##### **4.1.3.7.2.新增** {#18Vs8}

Ø原型设计

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739861516-910b7519-c7ea-44db-81b8-b60f10c14366.png "image")

Ø字段说明

| 元素名称 | 是否输入-类型 | 类型长度 | 是否必填 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| 版本号 | Y-下拉单选 | - | Y | 展示：不限、是、否；默认展示不限； |
| 是否强制更新 | Y-单选框 | - | Y | 默认为空，展示：是、否； |
| 更新内容 | Y-文本框 | 类型不限，100字以内 | Y | 若需要APP内换行展示，则输入时也必须换行输入； |
| APK上传 | 上传控件 | - | Y | 点击上传，显示“上传中”，上传成功后，将下载地址显示在输入框内； |



Ø功能描述

\(1\)点击新增，显示新增弹框；

\(2\)维护版本号：三个输入框均必填，且每个输入框最多三位数字；

\(3\)选择是否强制更新，选择“是”，表示该版本号为强制更新，“否”，标识该版本不需要强制更新；强制更新的版本号，若客户不更新无法正常使用客户端；

\(4\)维护更新内容，内容，长度不限；若需要换行显示，则输入时，也需换行；

\(5\)APK上传，点击选择查看本地文件，点击上传，弹框提示“上传中”，上传成功，弹框提示“上传成功”；

\(6\)点击保存，需要对所有字段进行校验，若存在为空，则提示“请完善【版本号/更新类型/更新内容】”或“请先上传APK！”；同时，需要对版本号进行校验，当前维护的版本号必须高于库中已存在的版本号，否则提示“版本号过低，请重新维护！”；

\(7\)点击取消或关闭，则弹框关闭；

##### **4.1.3.7.3.编辑** {#PC1Qj}

Ø原型设计

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739861731-c160f99f-6789-4a4a-b744-a5538f436202.png "image")

Ø字段说明

| 元素名称 | 是否输入-类型 | 类型长度 | 是否必填 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| 版本号 | N-仅显 | - | - | - |
| 是否强制更新 | N-仅显 | - | - | - |
| 更新内容 | Y-文本框 | 类型不限，100字以内 | Y | 若需要APP内换行展示，则输入时也必须换行输入； |
| APK上传 | N-仅显 | - | - | 下载地址显示在输入框内 |



Ø功能描述

\(1\)编辑状态下，无法对版本号、是否强制进行更改，同时无法上传APK，即仅能对更新内容进行编辑；

\(2\)点击保存，校验更新内容是否为空，为空，则提示“请完善更新内容！”；

\(3\)点击取消或关闭，则弹框消失；

##### **4.1.3.7.4.查看** {#K7oGX}

Ø原型设计

![](https://cdn.nlark.com/yuque/0/2019/png/460718/1576739861850-e6b88efe-3035-44b4-8af3-d5cad99c3b91.png "image")

Ø字段说明

| 元素名称 | 是否输入-类型 | 类型长度 | 是否必填 | 描述 |
| :--- | :--- | :--- | :--- | :--- |
| 版本号 | N-仅显 | - | - | - |
| 是否强制更新 | N-仅显 | - | - | - |
| 更新内容 | N-仅显 | - | - | - |
| APK上传 | N-仅显 | - | - | 下载地址显示在输入框内 |



Ø功能描述

\(1\)点击查看，进入查看弹框；

\(2\)查看版本号、是否强制更新、更新内容以及APK路径；

\(3\) 点击取消或关闭，则弹框消失；**  
**

# **5.**[**备忘录**]() {#YkgUl}

## **5.1.**[**邮件模板**]() {#7VnZk}

\(1\)理货邮件模板；（未提供）

\(2\)入库邮件模板；（未提供）

\(3\)发送方邮箱；（未提供）

## **5.2.**[**入库单**]() {#hlLJj}

\(1\)生成规则（未提供）

\(2\)入库单推送IWS校验字段以及规则（需要研发协助）

