---
title: App Store上线完整流程
date: 2016-03-05 17:25:33
tags:
---

经过多年的iOS开发，到现在一共上线了6款App到App Store。从iOS6到iOS9，每一次苹果系统的更新，App Store的上线流程都会有点相应的改变。对于上线App到App Store的这个流程现在已经是得心应手，现在利用周末这个闲暇的时间纪录一下完整的上传App到App Store的流程。

## 预先准备

在你开始将程序提交到App Store之前，您需要有一个开发者帐号、一个App ID、一个有效的证书以及一个有效的Provisioning Profiles。

###### Step 1:申请开发者帐号

如果您现在已有开发者帐号，那么恭喜您，您可以直接跳过此步骤直接进入下一步骤。苹果开发者帐号分为三种：个人开发者帐号、公司帐号、企业帐号。

**个人帐号（Individual）:**
* 费用：99美元一年
* App Store上架：是
* 最大uuid支持数：100
* 协作人数：1人（开发者自己）

说明：“个人”开发者可以申请升级“公司”，可以通过拨打苹果公司客服电话（400 6701 855）来咨询和办理。

** 公司帐号（Company）: **
* 费用：99美元一年
* App Store上架：是
* 最大uuid支持数：100
* 协作人数：多人

说明：允许多个开发者进行协作开发，比个人多一些帐号管理的设置，可设置多个Apple ID，分4种管理级别的权限。申请时需要填写公司的邓白氏编码（DUNS Number）。

** 企业帐号（Enterprise）: **
* 费用：299美元一年
* App Store上架：否
* 最大uuid支持数：不限制
* 协作人数：多人

说明：需要注意的是，企业账号开发的应用不能上线App Store，适合那些不希望公开发布应用的企业。同样，申请时也需要公司的邓白氏编码（DUNS Number）。

###### Step 2:App ID（应用ID）
App ID是识别不同应用程序的唯一标示符。每个app都需要一个App ID或者app标识。目前有两种类型的App标识：一个是精确的App ID（explicit App ID），一个是通配符App ID（wildcard App ID）。使用通配符的App ID可以用来构建和安装多个程序。尽管通配符App ID非常方便，但是一个精确的App ID也是需要的，尤其是当App使用iCloud 或者使用其他iOS功能的时候，比如Game Center、Push Notifications或者IAP。

###### Step 3:Distribution Certificate(发布证书)
iOS应用都有一个安全证书用于验证开发者身份和签名。为了可以向App Store提交app，你需要创建一个iOS provisioning profile 。首先需要创建一个distribution certificate（发布证书），过程类似于创建一个development certificate（开发证书）。如果你已经在实体设备上测试你的App，那么你对创建development certificate就已经很熟悉了。

###### Step 4:Provisioning Profile(配置文件)
一旦你创建了App ID和distribution certificate，你可以创建一个iOS provisioning profile以方便在App Store中销售你的App。Provisioning Profile主要分为开发配置文件和发布配置文件，发布配置文件中又分App Store配置文件和Ad Hoc配置文件。App Store类型的Provisioning Profile顾名思义是用于发布到App Store的配置文件。Ad Hoc的Provisioning Profile配置文件是用于发布应用内的测试包的，在应用还没有上线的时候需要发ipa给客户安装的时候需要用到，只需要获取到客户手机的UDID然后生成相应的Ad Hoc类型的Provisioning Profile文件然后打包发布即可。

