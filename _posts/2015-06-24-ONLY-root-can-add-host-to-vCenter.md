---
title: "VMware - add host into cluster"
description: "ONLY root account can add host into VMware cluster."
layout: post
tags: vmware, cluster, cloud, virtualization
category: tech
comments: yes
---

####License file download from standalone host 000.000.000.00 to vCenter Server failed due to exception: vim.fault.HostConnectFault.

I have a Host running on EXSi 5.1.0, a vCenter 5.5 running on it.

I had this problem for few days, googled lots of article, it's turned out: ONLY root account can add host into VMware cluster. 

#####References:
* [VMware Cmmunities](https://communities.vmware.com/message/2498032)
* [Downloading the license file fails 1017928](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1017928)
* [VMware Cmmunities](https://communities.vmware.com/message/1886324)