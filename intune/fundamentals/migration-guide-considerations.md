---
title: Consideraciones especiales sobre la migración
titleSuffix: Microsoft Intune
description: En este artículo se proporcionan aspectos especiales sobre la migración que deben considerarse antes de iniciar una campaña de migración a Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45e2985bcf01d635e964ee8785938c0d5df4e4af
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727615"
---
# <a name="special-migration-considerations"></a>Consideraciones especiales sobre la migración

Hay consideraciones especiales sobre la migración que se pueden aplicar en función del entorno del proveedor de MDM existente.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Borrado para el Programa de inscripción de dispositivos (DEP) de Apple

El Programa de inscripción de dispositivos (DEP) de Apple establece configuraciones de dispositivo que el usuario final no puede quitar. Para conservar las características de administración avanzada del DEP, el dispositivo se debe devolver al estado original (nuevo) mediante un borrado para inscribirlo en Intune.

Para seguir usando DEP para administrar los dispositivos en Intune, [configure la inscripción de dispositivos iOS con el Programa de inscripción de dispositivos](../enrollment/device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Pasos siguientes

[Fase 2: Campaña de migración](../migration-guide-campaign.md)
