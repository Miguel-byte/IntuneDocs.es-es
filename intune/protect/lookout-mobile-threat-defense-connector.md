---
title: Conector de Lookout MTD con Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo integrar Intune con Lookout Mobile Threat Defense (MTD) para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e16907f39fe8c6ea5e9a12f1e2b25026a5db225
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721323"
---
# <a name="lookout-mobile-endpoint-security-connector-with-intune"></a>Conector de Lookout Mobile Endpoint Security con Intune

Puede controlar el acceso del dispositivo móvil a recursos corporativos según la evaluación del riesgo que realice Lookout, una solución Mobile Threat Defense integrada con Microsoft Intune. El riesgo se evalúa basándose en la telemetría recopilada de dispositivos mediante el servicio de Lookout que incluye:
- Vulnerabilidades del sistema operativo
- Aplicaciones malintencionadas instaladas
- Perfiles de red malintencionados

Puede configurar directivas de acceso condicional basándose en la evaluación de riesgo de Lookout habilitada mediante las directivas de cumplimiento de Intune. Con la configuración puede permitir o bloquear dispositivos no compatibles basándose en las amenazas detectadas.

## <a name="how-do-intune-and-lookout-mobile-endpoint-security-help-protect-company-resources"></a>¿Cómo contribuye Lookout Mobile Threat Defense a proteger los recursos de la empresa?
La aplicación móvil Lookout, **Lookout for Work**, está instalada y se ejecuta en dispositivos móviles. Esta aplicación captura el sistema de archivos, la pila de red y la telemetría de aplicaciones y dispositivos cuando está disponible, después lo envía al servicio en la nube de Lookout para evaluar el riesgo del dispositivo para las amenazas móviles. Puede cambiar la clasificación del nivel de riesgo de las amenazas en la consola de Lookout para satisfacer sus requisitos.  

La directiva de cumplimiento en Intune incluye una regla para Mobile Threat Protection de Lookout basada en la evaluación del riesgo de Lookout. Cuando esta regla está habilitada, Intune evalúa la conformidad del dispositivo con la directiva que habilitó.

Si se detecta que el dispositivo no es compatible, puede bloquearse el acceso a recursos como Exchange Online y SharePoint Online. Los usuarios de dispositivos bloqueados reciben los pasos para resolver el problema y volver a obtener acceso. Las instrucciones se inician desde la aplicación Lookout for Work.

## <a name="supported-platforms"></a>Plataformas compatibles  
Las siguientes plataformas son compatibles con Lookout cuando se inscriben en Intune:
* **Android 4.1 y versiones posteriores**  
* **iOS 8 y versiones posteriores**  

Para información adicional sobre la compatibilidad de lenguaje y plataforma, visite el [sitio web de Lookout](https://personal.support.lookout.com/hc/articles/114094140253).  

## <a name="prerequisites"></a>Requisitos previos
* Suscripción de empresa a Lookout Mobile Endpoint Security  
* Suscripción a Microsoft Intune
* Azure Active Directory Premium
* Enterprise Mobility and Security (EMS) E3 o E5, con licencias asignadas a los usuarios.  

Para obtener más información, consulte [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security).

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Estos son los escenarios comunes cuando se usa Mobile Endpoint Security con Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Control del acceso basado en amenazas de aplicaciones malintencionadas
Cuando las aplicaciones malintencionadas como malware se detectan en dispositivos, puede bloquear los dispositivos de la siguiente manera hasta que la amenaza se resuelva:
* Conectarse al correo electrónico corporativo
* Sincronizar los archivos corporativos mediante la aplicación OneDrive para el trabajo
* Acceder a las aplicaciones de empresa

**Bloquear cuando se detectan aplicaciones malintencionadas:**

![Imagen conceptual de directiva que bloquea el acceso por contener aplicaciones malintencionadas](./media/lookout-mobile-threat-defense-connector/malicious-apps-blocked.png)

**Acceso concedido tras la corrección:**

![Imagen conceptual que muestra el acceso que se concede a los dispositivos después de la corrección](./media/lookout-mobile-threat-defense-connector/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Control del acceso basado en amenazas a la red
Detecte amenazas para la red como ataques de tipo "Man in the middle" y proteja el acceso a las redes Wi-Fi según el riesgo del dispositivo.

**Bloquear el acceso de red a través de Wi-Fi:**

![Imagen que muestra el bloqueo de acceso de Wi-Fi basándose en amenazas de red](./media/lookout-mobile-threat-defense-connector/network-wifi-blocked.png)

**Acceso concedido tras la corrección:**

![Imagen conceptual del acceso condicional que permite el acceso después de la corrección](./media/lookout-mobile-threat-defense-connector/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Control del acceso a SharePoint Online basado en amenazas a la red

Detecte amenazas para la red como ataques de tipo Man-in-the-middle y evite la sincronización de archivos corporativos según el riesgo del dispositivo.

**Bloqueo de SharePoint Online cuando se detectan amenazas a la red:**

![Imagen conceptual de bloqueo del acceso a SharePoint Online](./media/lookout-mobile-threat-defense-connector/network-spo-blocked.png)


**Acceso concedido tras la corrección:**

![Imagen conceptual que muestra cómo se permite el acceso tras la corrección de la amenaza de red](./media/lookout-mobile-threat-defense-connector/network-spo-unblocked.png)

## <a name="next-steps"></a>Pasos siguientes
Estos son los principales pasos para implementar esta solución:
1. [Configurar la integración a Lookout](lookout-mtd-connector-integration.md)
2. [Habilitar el conector Mobile Threat Defense en Intune](mtd-connector-enable.md)
3. [Agregar y asignar la aplicación Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
4. [Crear la directiva de cumplimiento de dispositivos de Lookout](mtd-device-compliance-policy-create.md)
