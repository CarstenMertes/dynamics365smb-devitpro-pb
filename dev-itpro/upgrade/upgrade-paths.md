---
title: Supported upgrade paths to Business Central on-premises
description: Provides an overview of the different upgrade paths for Business Central on-premises across versions.
author: jswymer
ms.topic: upgrade-and-migration-article
ms.author: jswymer
ms.date: 04/09/2025
ms.reviewer: jswymer
---

# Supported upgrade paths to Business Central releases

[!INCLUDE[prod_short](../developer/includes/prod_short.md)] on-premises is available in several release versions. You can upgrade an existing Dynamics NAV or Business Central solution to any of these releases. Depending on your solution's current version, it might not be possible to upgrade directly to a particular release. You might have to upgrade indirectly through an intermediate release, before upgrading to the target release.  

<!--

Whether you can upgrade directly to a release will depend on the source version. For some targets, there's an indirect path through an intermediate version. The path that you must take to upgrade to the new Oracle Database 11g release depends on the release number of your current database. It might not be possible to directly upgrade from your current release of Oracle Database to the latest release. Depending on your current release, you might be required to upgrade through one or more intermediate releases to upgrade to the new Oracle Database 11g release.

-->

The following sections provide the supported upgrade paths to the different [!INCLUDE[prod_short](../developer/includes/prod_short.md)] releases.

> [!NOTE]
> - Minor updates are regularly available for each release wave. Not all minor updates between two releases are compatible. Upgrade to a release update that's compatible with your current version to avoid problems. Learn more in [Dynamics 365 Business Central Upgrade Compatibility Matrix](./upgrade-v14-v15-compatibility.md?branch=2020rw1-upgrade).
> - Starting in 2025 release wave 1 (v26), the direct upgrade from Business Central 2019 (v14) to the latest release won't be supported. The supported upgrade path will be through 2024 release wave 2 (v25). Learn more in [Deprecated features in the platform - clients, server, and database](deprecated-features-platform.md#changes-in-2025-release-wave-1-version-260)

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2025 release wave 1 (v26)

|  Source version  |  Path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)] (version 8)</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)] (version 9)</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)] (version 10)</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)] (version 11)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] October 2018 (version 13)</li></ul>|<ol><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (version 14)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2024 release wave 2 (version 25)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2025 release wave 1 (version 26)</li></ol>This path requires you convert your application from C/AL to AL.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (version 14)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2019 release wave 2 (version 15)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1 (version 16)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 2 (version 17)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1 (version 18)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2 (version 19)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1 (version 20)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 2 (version 21)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 1 (version 22)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 2 (version 23)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2024 release wave 1 (version 24)</li></ul>|<ol><li>Version 25</li><li>Version 26</li></ol>|
|<ul><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2024 release wave 2 (version 25)</li></ul>|Direct to version 26|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2024 release wave 2 (v25)

|  Source version  |  Path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)] (version 8)</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)] (version 9)</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)] (version 10)</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)] (version 11)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] October 2018 (version 13)</li></ul>|<ol><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (version 14)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2024 release wave 2 (version 25)</li></ol>This path requires you convert your application from C/AL to AL.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (version 14)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2019 release wave 2 (version 15)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1 (version 16)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 2 (version 17)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1 (version 18)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2 (version 19)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1 (version 20)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 2 (version 21)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 1 (version 22)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 2 (version 23)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2024 release wave 1 (version 24)</li></ul>|Direct to version 25|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2024 release wave 1 (v24)

|  Source version  |  Path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)] (version 8)</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)] (version 9)</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)] (version 10)</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)] (version 11)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] October 2018 (version 13)</li></ul>|<ol><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (version 14)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2024 release wave 1 (version 24)</li></ol>This path requires you convert your application from C/AL to AL.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (version 14)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2019 release wave 2 (version 15)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1 (version 16)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 2 (version 17)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1 (version 18)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2 (version 19)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1 (version 20)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 2 (version 21)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 1 (version 22)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 2 (version 23)</li></ul>|Direct to version 24|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 2 (v23)

|  Source version  |  Path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)] (version 8)</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)] (version 9)</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)] (version 10)</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)] (version 11)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] October 2018 (version 13)</li></ul>|<ol><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (version 14)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 2 (version 23)</li></ol>This path requires you convert your application from C/AL to AL.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (version 14)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2019 release wave 2 (version 15)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1 (version 16)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 2 (version 17)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1 (version 18)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2 (version 19)</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1 (version 20)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 2 (version 21)</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 1 (version 22)</li></ul>|Direct to version 23|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2023 release wave 1 (v22)

|  Source version  |  Path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Indirect. Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14 first.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v15</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v16</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v17</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v18</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v19</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v20</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v21</li></ul>|Direct|


## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 2 (v21)

|  Source version  |  Path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Indirect. Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14 first.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v15</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v16</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v17</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v18</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v19</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v20</li></ul>|Direct|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1 (v20)

|  Source version  |  Path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Indirect. Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14 first.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v15</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v16</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v17</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v18</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v19</li></ul>|Direct|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2 (v19)

|  Source version  |   Upgrade path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Indirect. Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14 first.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v15</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v16</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v17</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v18</li></ul>|Direct|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1 (v18)

|  Source version  |   Upgrade path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Indirect. Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14 first.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v15</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v16</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v17</li></ul>|Direct|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 2 (v17)

|  Source version  |   Upgrade path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Indirect. Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14 first.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v15</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v16</li></ul>|Direct|

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 1 (v16)

|  Source version  |   Upgrade path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Indirect. Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14 first.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14</li><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v15</li></ul>|Direct|

[!INCLUDE [upgrade-16](../includes/upgrade-16.md)]

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2019 release wave 2 (v15)

|  Source version  |   Upgrade path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Indirect. Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14 first.|
|<ul><li> [!INCLUDE[prod_short](../developer/includes/prod_short.md)] v14</li></ul>|Direct |

[!INCLUDE [upgrade-15](../includes/upgrade-15.md)]

## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Spring 2019 (v14)

[!INCLUDE [upgrade-14](../includes/upgrade-14.md)]

|  Source version  |   Upgrade path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li><li>[!INCLUDE[prod_short](../developer/includes/prod_short.md)] v13</li></ul>|Direct|

<!--## Upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] October 2018 (v13)

|  Source version  |  Upgrade path  |
|------------|--------------|
|<ul><li> [!INCLUDE[navcrete](../developer/includes/navcrete_md.md)]</li><li>[!INCLUDE[navcorfu](../developer/includes/navcorfu_md.md)]</li><li>[!INCLUDE[nav2017](../developer/includes/nav2017.md)]</li><li>[!INCLUDE[nav2018_md](../developer/includes/nav2018_md.md)]</li></ul>|Direct|
-->
## Related information

[Upgrading to Business Central 2025 release wave 1](upgrade-overview-v26.md)  
[Upgrading to Business Central 2024 release wave 2](upgrade-overview-v25.md)  
[Upgrading to Business Central 2024 release wave 1](upgrade-overview-v24.md)  
[Upgrading to Business Central 2023 release wave 2](upgrade-overview-v23.md)  
[Upgrading to Business Central 2023 release wave 1](upgrade-overview-v22.md)  
[Upgrading to Business Central 2022 release wave 2](upgrade-overview-v21.md)  
[Upgrading to Business Central 2022 release wave 1](upgrade-overview-v20.md)  
[Upgrading to Business Central 2021 release wave 2](upgrade-overview-v19.md)  
[Upgrading to Business Central 2021 release wave 1](upgrade-overview-v18.md)  
[Upgrading to Business Central Spring 2019](upgrading-to-business-central-on-premises.md)  
[Migrate to Business Central Online from Business Central On-premises](../administration/migrate-business-central-on-premises.md)  
[Migrating On-Premises Data to Business Central Online](../administration/migrate-data.md)  

[!INCLUDE [footer-banner](../includes/footer-banner.md)]
