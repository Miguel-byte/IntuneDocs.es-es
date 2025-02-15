---
title: Resolver el conjunto de restricciones de punto de acceso en Intune
description: Eche un vistazo a los tres mensajes comunes de las directivas de restricción de punto de acceso de Intune y aprenda a resolverlos
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: aefde274ec7ca925d45dd101ee0ebef1083f7f19
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "55851277"
---
# <a name="resolve-access-point-restrictions"></a>Resolver restricciones de punto de acceso

Es posible que las organizaciones restrinjan las ubicaciones desde las que los dispositivos acceden a los datos corporativos.
Para configurar estas *restricciones de punto de acceso*, se especifican y se establecen unas ubicaciones de red autorizadas.  

Al intentar conectarse a una red no reconocida o no aprobada, puede que reciba uno o varios de los siguientes mensajes:

* Las restricciones de punto de acceso no están configuradas.
* No está conectado a una red autorizada.
* Se produjo un error y no se pudieron aplicar las restricciones de punto de acceso.

 En las tablas siguientes se muestra cada mensaje, su significado y cómo acceder a los recursos de trabajo de nuevo.

## <a name="access-point-restrictions-not-set-up"></a>Restricciones de punto de acceso no configuradas  
| Mensaje del Portal de empresa | Significado del mensaje | Haga lo siguiente                                                               
|------------------------|--------------------------|--------------------------|
| **Access point restrictions are not set up – Access point restrictions are active and must be set up.** (Las restricciones de punto de acceso no están configuradas: las restricciones de punto de acceso están activas y deben configurarse) | La empresa ha aplicado restricciones de punto de acceso en el dispositivo. Según esta opción, la aplicación Portal de empresa tiene que comprobar algunos valores de configuración de red en el dispositivo. | Pulse en **Resolver**. La aplicación Portal de empresa comprobará que está conectado a una red autorizada de la empresa. |

## <a name="not-connected-to-an-approved-network"></a>No conectado a una red autorizada  

| Mensaje del Portal de empresa | Significado del mensaje | Haga lo siguiente                                                                   
|------------------------|-----------------------------------|--------------------------|
| **Device is not connected to an approved network – Connect to an approved wireless network.** (El dispositivo no está conectado a una red autorizada: conéctese a una red inalámbrica autorizada) | Está conectado a una red que no está autorizada para acceso en el trabajo. Mientras esté conectado a esta red, no podrá acceder al correo electrónico del trabajo, las aplicaciones y otros recursos protegidos de la empresa. | Conéctese a una red autorizada por la empresa. Después, pulse en **Resolver** para volver a intentarlo. |

## <a name="restrictions-couldnt-be-enforced"></a>No se pudieron aplicar restricciones  

| Mensaje del Portal de empresa | Significado del mensaje | Haga lo siguiente                                                                      
|------------------------|-----------------------------------|--------------------------|
| **Access point restrictions could not be enforced – Company Portal encountered an error.** (No se pudieron aplicar restricciones de punto de acceso: error en el Portal de empresa) | Intune no puede determinar si se ha conectado a una red autorizada. Este error puede deberse a una mala conectividad de red, poca batería, modo de ahorro de batería o un error del Portal de empresa. | Compruebe que la intensidad de la señal de red es alta. Desactive el modo de ahorro de batería y asegúrese de que a la batería le queda al menos un 30 % de duración. Después, pulse en **Resolver** para volver a intentarlo. 

¿Sigue necesitando ayuda? Le recomendamos ponerse en contacto con el equipo de soporte técnico de su empresa. Para obtener información de contacto específica, vaya al [sitio web de Portal de empresa](https://portal.manage.microsoft.com/#HelpDeskDialog).
