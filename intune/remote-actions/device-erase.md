---
title: Borrar el contenido de un dispositivo macOS
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo borrar todos los datos, incluido el sistema operativo, de un dispositivo macOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e2f4ce1295d4a3f2250988d25246c532ff2cdd73
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728239"
---
# <a name="erase-all-data-from-a-macos-device"></a>Borrar todos los datos de un dispositivo macOS

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede borrar todos los datos de un dispositivo macOS, incluido el sistema operativo. El dispositivo también se eliminará de la administración de Intune. No se proporcionará ninguna advertencia al usuario final.

1. En [Azure Portal de Intune](https://aka.ms/intuneportal), elija **Dispositivos** > **Todos los dispositivos** > elija el dispositivo cuyo contenido desee borrar.
![Captura de pantalla](./media/device-erase/choosedevice.png)
2. Haga clic en **Más** > **Borrar** > proporcione un número de 6 dígitos para el **PIN de recuperación**. Este es el PIN que debe proporcionar al usuario para que pueda volver a instalar el sistema operativo en su dispositivo. No olvide anotar este PIN porque no podrá verlo una vez completada la acción de borrado.
![Captura de pantalla](./media/device-erase/providepin.png)
3. Haga clic en **Aceptar** para borrar el dispositivo.
