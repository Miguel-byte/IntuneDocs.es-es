---
title: Página Estado del inquilino de Microsoft Intune
titleSuffix: Microsoft Intune
description: Use la página Estado del inquilino de Intune para ver detalles importantes del inquilino sin salir del portal de Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b55623dec2a89df700da8c0adb1c64e7e754043f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721700"
---
# <a name="use-the-intune-tenant-status-page"></a>Uso de la página de estado del inquilino de Intune
La página de estado del inquilino de Microsoft Intune es un centro donde puede ver detalles importantes y actuales sobre el inquilino. Entre estos detalles se incluyen la disponibilidad y el uso de la licencia, el estado del conector y comunicaciones importantes sobre el servicio Intune.  

Para ver el panel, inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y, a continuación, seleccione **Estado de inquilino**.  *Estado de inquilino* aparece en **Ayuda y soporte técnico**.  

La página se divide en tres pestañas:

## <a name="tenant-details"></a>Detalles del inquilino
Detalles del inquilino proporciona información de un vistazo sobre el inquilino. Vea detalles como el nombre y la ubicación del inquilino, la entidad de MDM y el número de versión del servicio de inquilinos. El número de versión del servicio es un vínculo que abre el artículo *Novedades de Intune* en Microsoft Docs. En *Novedades*, puede consultar información sobre las últimas características y actualizaciones del servicio Intune.  

En esta pestaña también encontrará información básica sobre las licencias disponibles y cuántas se han asignado a los usuarios. No se muestran las licencias de los dispositivos.

## <a name="connector-status"></a>Estado del conector
Estado del conector es una ubicación única para revisar el estado de todos los conectores disponibles para Intune.  

Los conectores son:
- **Conexiones que se configuran a servicios externos**. Por ejemplo, el servicio *Programa de Compras por Volumen de Apple* o el servicio *Windows Autopilot*.  El estado de este tipo de conector se basa en la hora de la última sincronización correcta.
- **Certificados o credenciales necesarios para conectarse a un servicio externo no administrado**, como certificados de *Apple Push Notification Services* (APN). El estado de este tipo de conector se basa en la marca de tiempo de expiración del certificado o la credencial.  

Al abrir la pestaña *Estado del conector*, los conectores incorrectos se muestran en la parte superior de la lista. Luego aparecen los conectores con advertencias y, después, la lista de conectores correctos. Los conectores que todavía no se han configurado aparecen al final como *No habilitado*.

Si hay más de un conector de cualquier tipo, el estado es un resumen de todos esos conectores. El estado mínimo de cualquier conector se usa como estado del grupo.  

**Estado del conector**:
- **Incorrecto**:
  - El certificado o la credencial ha expirado
  - La última sincronización fue hace tres o más días
- **Advertencia**:
  - El certificado o la credencial expira en siete días
  - La última sincronización fue hace más de un día
- **Correcto**:
  - El certificado o la credencial no expira en los próximos siete días
  - La última sincronización fue hace menos de un día  

Cuando se selecciona un conector de la lista, el portal presenta la página del portal que es relevante para ese conector. En la página de conectores puede ver el estado de los conectores configurados anteriormente, o bien seleccionar opciones para agregar o crear un nuevo conector de ese tipo.

Por ejemplo, si selecciona el conector **Fecha de caducidad de VPP**, se abre la página **Tokens del programa de compras por volumen de iOS**, donde puede ver más detalles sobre ese conector. También puede crear una nueva configuración o editar y solucionar problemas con una ya existente.

## <a name="service-health-dashboard"></a>Panel de Service Health  
En el panel de Service Health puede ver detalles de los *incidentes en el servicio* que afectan a su inquilino y *noticias de Intune* que proporcionan información sobre actualizaciones y cambios planeados.

### <a name="intune-service-health"></a>Estado del servicio Intune
Vea detalles de incidentes activos y avisos sin tener que ir al panel de Estado del servicio Microsoft 365 ni al Centro de mensajes, que se encuentran en el [Centro de administración de Microsoft 365](https://admin.microsoft.com). Solo se muestran los incidentes que afectan a su inquilino.  

Al seleccionar un incidente, los detalles de este se presentan directamente en la página Estado del inquilino. Para ver avisos e incidentes pasados, seleccione **See past Incidents/Advisories** (Ver incidentes y avisos pasados). Se abre el centro de administración de Microsoft 365, donde puede ver los avisos e incidentes del inquilino de los últimos 30 días.  

Para ver información del *Estado del servicio Intune*, la cuenta debe tener el rol **Administrador global** o **Administrador de servicios** en Azure Active Directory o el Centro de administración de Microsoft 365. Para asignar estos permisos, inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) con permisos de Administrador global. Seleccione **Usuarios > Usuarios activos** y luego seleccione la cuenta que requiere acceso. Seleccione **Editar** en los roles, seleccione *Administrador de servicios* o *Administrador global* y luego seleccione **Guardar** para asignar los permisos.  

Las preferencias de comunicación de Estado del servicio Intune solo se pueden establecer a través del centro de administración de Microsoft 365.

### <a name="intune-news"></a>Noticias de Intune  
Vea comunicaciones informativas del equipo del servicio Intune sin tener que ir al centro de mensajes de Office. Las comunicaciones incluyen mensajes sobre los cambios que se han producido recientemente en el servicio Intune o que están en camino para el inquilino.  

De forma predeterminada, se muestran los 10 mensajes más recientes y activos. Para ver mensajes más antiguos, seleccione **Ver mensajes anteriores** para abrir el *Centro de mensajes* en el Centro de administración de Microsoft 365.  

Para ver información de Noticias de Intune, la cuenta debe tener el rol **Administrador global** o **Administrador de servicios** en Azure Active Directory, o bien el rol **Lector del Centro de mensajes**  en el Centro de administración de Microsoft 365.  Para asignar este permiso, inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) con permisos de administrador. Seleccione **Usuarios > Usuarios activos** y luego seleccione la cuenta que requiere acceso. Seleccione **Editar** en *Roles*, seleccione *Administrador de comunicaciones de Teams*  y luego seleccione **Guardar** para asignar los permisos.  

Las preferencias de comunicación de Noticias de Intune solo se pueden establecer a través del centro de administración de Microsoft 365.
