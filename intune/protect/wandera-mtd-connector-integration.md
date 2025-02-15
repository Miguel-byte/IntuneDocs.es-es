---
title: Configuración de la integración de Wandera Mobile Threat Protection con Intune
titleSuffix: Intune on Azure
description: Cómo configurar la solución Wandera Mobile Threat Protection con Microsoft Intune para controlar el acceso de los dispositivos móviles a los recursos corporativos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bf8fd189e50a704e96fc24d0804c5c5d6f91bb4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728226"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Integración de Wandera Mobile Threat Protection con Intune  

Complete los pasos siguientes para integrar la solución Wandera Mobile Threat Defense con Intune.  

## <a name="before-you-begin"></a>Antes de comenzar  

Antes de iniciar el proceso para integrar Wandera con Intune, asegúrese de que cumple los siguientes requisitos previos:
- Suscripción a Microsoft Intune  
- Credenciales de administrador de Azure Active Directory para conceder los permisos siguientes:  
  - Iniciar sesión y leer el perfil del usuario  
  - Obtener acceso al directorio con el usuario que tiene la sesión iniciada  
  - Leer datos de directorio  
  - Enviar información del dispositivo a Intune  

- Suscripción a Wandera:
  - Una o varias cuentas de Wandera que tienen licencia para EMM Connect  
  - Una cuenta con privilegios de superadministrador en Wandera  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Autorización de aplicaciones de Wandera Mobile Threat Defense  

El proceso de autorización de aplicaciones de Wandera Mobile Threat Defense:  
- Permita que el servicio Wandera Mobile Threat Defense comunique a Intune la información relacionada con el estado de mantenimiento del dispositivo.  
- Wandera se sincroniza con la pertenencia a grupos de inscripción de Azure AD para rellenar la base de datos de su dispositivo.  
- Permita que el portal de administración RADAR de Wandera use Inicio de sesión único (SSO) de Azure AD.  
- Permita que la aplicación de Wandera Mobile Threat Defense inicie sesión con SSO de Azure AD.  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Configuración de la integración de Wandera Mobile Threat Defense  
La configuración de *EMM Connect* para Wandera requiere un proceso de configuración único que completa tanto en las consolas de Intune como en las de Wandera. El proceso de configuración tarda aproximadamente 15 minutos. Puede completar la configuración sin coordinación con su representante de cuenta o soporte técnico.  

### <a name="enable-support-for-wandera-in-intune"></a>Habilitar la compatibilidad con Wandera en Intune
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y vaya a **Cumplimiento de dispositivos** > **Mobile Threat Defense** > y seleccione **Agregar**.

2. En la página **Agregar conector**, use la lista desplegable y seleccione **Wandera**. Después seleccione **Crear**.  

3. En el panel Mobile Threat Defense, seleccione el conector MTD de **Wandera** en la lista de conectores para abrir el panel *Editar conector*. Seleccione **Open the Wandera admin console** (Abrir la consola de administración de Wandera) para abrir [RADAR](https://radar.wandera.com/login), la consola de administración de Wandera, e inicie sesión. 

4. En la consola de Wandera, vaya a **Configuración** > **Integración de EMM** y seleccione la pestaña **EMM Connect**. Use la lista desplegable *Proveedor de EMM* y seleccione *Microsoft Intune*.

   ![Seleccionar Intune](./media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. Seleccione **Conceder permisos** para abrir una conexión con el portal de Intune. Inicie sesión con sus credenciales de administrador de Intune, active la casilla y, a continuación, **acepte** la solicitud de permisos.  

   ![Aceptar permisos](./media/wandera-mtd-connector-integration/permissions.png) 

6. Wandera completa la conexión y le devuelve a la consola de administración RADAR. Repita el proceso para **conceder** acceso para configuraciones adicionales, según sea necesario.  

   ![Integraciones y permisos](./media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. Mientras está en la consola RADAR, copie el nombre del grupo **SyncOnly** que aparece debajo de **Etiqueta EMM**. Usará este nombre para configurar un grupo en Intune para la sincronización con Wandera.

   ![Integraciones y permisos](./media/wandera-mtd-connector-integration/sync-group-name.png) 

8. Vuelva a la consola de [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y edite el conector MTD de Wandera. Establezca los conmutadores disponibles en **Activado** y **guarde** la configuración.  

   ![Habilitar Wandera](./media/wandera-mtd-connector-integration/enable-wandera.png) 

Intune y Wandera ya están conectados.  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Configurar las aplicaciones y el grupo de sincronización de Wandera  
Para implementar Wandera, agregará las aplicaciones móviles de Wandera para las plataformas que use (iOS y Android) a Intune y las asignará a un grupo específico para la sincronización, el grupo *SyncOnly*. 

Las siguientes secciones y procedimientos lo guiarán en este proceso.

Para obtener más información sobre este proceso en Wandera, inicie sesión en [RADAR](https://radar.wandera.com/login) de Wandera. Vaya a **Configuración** > **Integración de EMM**, seleccione la pestaña **App Push** (Inserción de aplicación) y, a continuación, seleccione **Microsoft Intune**. La pestaña App Push (Inserción de aplicación) se actualiza con instrucciones que son específicas de Intune.  

### <a name="add-the-wandera-apps"></a>Agregar las aplicaciones de Wandera  
Cree aplicaciones cliente en Intune para implementar la aplicación de Wandera en dispositivos Android e iOS. Consulte [Agregar y asignar aplicaciones de Mobile Threat Defense (MTD) con Intune](mtd-apps-ios-app-configuration-policy-add-assign.md) para los procedimientos y detalles personalizados específicos de las aplicaciones de Wandera.  

Después de crear las aplicaciones, vuelva aquí para crear el grupo de sincronización y asignar las aplicaciones.  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>Cree el grupo de sincronización y asigne las aplicaciones

1. Obtenga el nombre del grupo **SyncOnly** que aparece debajo de **Etiqueta EMM** desde dentro de la consola RADAR de Wandera. Podría haber guardado este nombre durante el paso 7 mientras se [habilitaba la compatibilidad con Wandera en Intune](#enable-support-for-wandera-in-intune). Use este nombre como nombre del grupo en Intune para la sincronización de Wandera.  

2. En la consola de Intune, vaya a **Grupos** y seleccione **Nuevo grupo**. Especifique lo siguiente para configurar el grupo de sincronización para que Wandera lo use:
   - **Tipo de grupo**: **Seguridad**
   - **Nombre de grupo**: especifique el nombre **SyncOnly** que recuperó de la consola de administración RADAR de Wandera.

   ![configurar el grupo de sincronización](./media/wandera-mtd-connector-integration/configure-sync-group.png)

3. Seleccione **Miembros** y asigne grupos donde se incluyan los dispositivos Android e iOS que desea usar con Wandera.

4. Seleccione **Crear** para guardar el grupo.

Para obtener más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](../apps/apps-deploy.md)

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Asignar las aplicaciones de Wandera al grupo de sincronización  
Repita el siguiente procedimiento para la aplicación de Wandera que creó para iOS y Android.

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y vaya a **Aplicaciones cliente** > **Aplicaciones** y seleccione la aplicación de Wandera.  

2. Seleccione **Asignaciones** y, a continuación, **Agregar grupo**.  

3. En el panel *Agregar grupo*, para *Tipo de asignación*, seleccione **Obligatorio**.

4. Seleccione **Grupos incluidos** y, a continuación, **Seleccionar grupos para incluir**. Especifique el grupo que creó para la sincronización de Wandera y, a continuación, haga clic en **Seleccionar** > **Aceptar** > **Aceptar**. Seleccione **Guardar** para completar la asignación de grupo.  
 

## <a name="next-steps"></a>Pasos siguientes  
Ahora que ha configurado la integración, puede empezar a configurar directivas y el acceso condicional avanzado, y ver informes en la consola de administración de Wandera. Para obtener más información sobre cómo administrar y configurar Wandera, consulte la [guía de introducción del Centro de soporte técnico](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started) en la documentación de Wandera.  
 