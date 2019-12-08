# 移动应用安全验证标准

MASVS可用于建立对移动应用程序安全性的置信度。制定需求时考虑了以下目标：

- 用作度量标准-提供安全标准，开发人员和应用程序所有者可以将现有移动应用程序与之进行比较；
- 用作指导-在移动应用开发和测试的所有阶段提供指导；
- 在采购过程中使用-为移动应用安全性验证提供基准。

## Mobile AppSec 模型

MASVS定义了两个安全验证级别（MASVS-L1和MASVS-L2），以及一组反向工程弹性要求（MASVS-R）。 MASVS-L1包含所有移动应用程序都建议使用的通用安全要求，而MASVS-L2应该应用于处理高度敏感数据的应用程序。如果防止客户端威胁是设计目标，则MASVS-R涵盖可以应用的其他保护性控件。

满足MASVS-L1中的要求将产生一个遵循安全最佳实践的安全应用程序，并且不会遭受常见漏洞的困扰。 MASVS-L2添加了其他深度防御控件（如SSL固定），从而使应用程序可以抵抗更复杂的攻击-假设移动操作系统的安全控件完好无损，并且最终用户不被视为潜在的对手。满足MASVS-R中全部或部分软件保护要求有助于在最终用户恶意和/或移动操作系统受到威胁的情况下阻止特定的客户端威胁。

**I：尽管我们建议在每个应用程序中实施MASVS-L1控件，但是否实施控件最终应是基于风险的决策，该决策应与企业所有者沟通。**

**II：请注意，MASVS-R中列出的软件保护控件以及《 OWASP移动安全性测试指南》中所述的软件保护控件最终都可以被绕过，绝不能用作安全控件的替代品。相反，它们旨在向也满足MASVS-L1或MASVS-L2中的MASVS要求的应用程序添加其他特定于威胁的保护性控件。**

！[验证级别]（images / masvs-levels-new.jpg）

### 文档结构

MASVS的第一部分包含对安全模型和可用验证级别的描述，然后是有关如何在实践中使用该标准的建议。在第二部分中列出了详细的安全要求以及对验证级别的映射。根据技术目标/范围，将需求分为八类（V1至V8）。在整个MASVS和MSTG中使用以下术语：

-*要求类别：* MASVS-Vx，例如MASVS-V2：数据存储和隐私
-*要求：* MASVS-Vx.y，例如MASVS-V2.2：“没有敏感数据写入应用程序日志。”
  
### 详细验证级别

#### MASVS-L1：标准安全性

实现MASVS-L1的移动应用程序遵循移动应用程序安全性最佳做法。它满足了代码质量，敏感数据处理以及与移动环境交互方面的基本要求。必须有一个测试过程来验证安全控制。此级别适用于所有移动应用程序。

#### MASVS-L2：纵深防御

MASVS-L2引入了超出标准要求的高级安全控制。为了实现MASVS-L2，必须存在威胁模型，并且安全性必须是应用程序体系结构和设计的组成部分。基于威胁模型，应该已经选择并成功实施了正确的MASVS-L2控件。此级别适用于处理高度敏感数据的应用程序，例如移动银行应用程序。

#### MASVS-R：抵抗逆向工程和篡改的弹性

该应用程序具有最先进的安全性，还可以抵抗明确定义的特定客户端攻击，例如篡改，修改或反向工程以提取敏感代码或数据。这样的应用程序要么利用硬件安全功能，要么利用足够强大且可验证的软件保护技术。 MASVS-R适用于处理高度敏感数据的应用程序，并且可以用作保护知识产权或防篡改应用程序的一种方式。

### 推荐使用

可以根据事先的风险评估和所需的总体安全级别，针对MASVS L1或L2验证应用程序。 L1适用于所有移动应用程序，而L2通常建议用于处理更敏感数据和/或功能的应用程序。 MASVS-R（或其一部分）可用于验证针对特定威胁的弹性，例如重新包装或提取敏感数据，以及适当的安全验证。

总之，可以使用以下验证类型：

- MASVS-L1
- MASVS-L1 + R
- MASVS-L2
- MASVS-L2 + R


不同的组合反映了不同级别的安全性和弹性。 目的是要具有灵活性：例如，出于可用性的原因，移动游戏可能不保证添加MASVS-L2安全控制（例如2要素身份验证），但是在防止篡改方面存在强烈的业务需求。
<div style="page-break-after: always;">
</div>

#### 选择哪种验证类型

满足MASVS L2的要求可以提高安全性，同时又增加了开发成本，并有可能使最终用户体验恶化（传统的权衡取舍）。通常，从风险与成本的角度来看（即，由于机密性或完整性受到损害而导致的潜在损失高于其他安全控制措施带来的损失），应在任何时候将L2用于应用程序。风险评估应是应用MASVS之前的第一步。

##### 举例

###### MASVS-L1

- 所有移动应用。 MASVS-L1列出了可以遵循的最佳安全实践，对开发成本和用户体验产生了合理的影响。将MASVS-L1中的要求应用于任何不符合较高级别之一的应用。

###### MASVS-L2

- 保健行业：存储个人身份信息的移动应用程序，这些信息可用于身份盗窃，欺诈性付款或各种欺诈方案。对于美国医疗保健部门，合规性考虑因素包括《健康保险可移植性和责任法案》（HIPAA）隐私权，安全性，违约通知规则和患者安全规则。

- 金融行业：可以访问高度敏感的信息（例如信用卡号，个人信息）或允许用户转移资金的应用。这些应用程序需要其他安全控制措施，以防止欺诈。金融应用需要确保遵守支付卡行业数据安全标准（PCI DSS），《格莱姆·里奇·布利利法案》和《萨班斯-奥克斯利法案》（SOX）。

###### MASVS L1 + R

- 以知识产权（IP）保护为业务目标的移动应用程序。 MASVS-R中列出的弹性控件可用于增加获取原始源代码和阻止篡改/破解所需的工作。

- 游戏产业：竞争激烈的在线游戏等对防止游戏和作弊至关重要的游戏。作弊是在线游戏中的一个重要问题，因为大量作弊会导致不满的玩家群体，并最终导致游戏失败。 MASVS-R提供基本的防篡改控件，以帮助增加作弊者的工作量。

###### MASVS L2 + R

- 金融业：允许用户转移资金的在线银行应用程序，其中代码注入和在受损设备上的检测等技术会带来风险。在这种情况下，可以使用MASVS-R的控件来阻止篡改，从而提高了恶意软件作者的标准。

- 根据设计，所有需要将敏感数据存储在移动设备上并且同时必须支持各种设备和操作系统版本的移动应用程序。在这种情况下，弹性控制可用作深度防御措施，以增加旨在提取敏感数据的攻击者的工作量。

- 进行应用内购买的应用最好应使用服务器端和MASVS-L2控件来保护付费内容。但是，在某些情况下，不可能使用服务器端保护。在那些情况下，应另外使用MASVS-R控件，以增加倒车和/或篡改的力度。