---
title: Integración de Jamf Pro con Microsoft Intune para cumplimiento
titleSuffix: Microsoft Intune
description: Use directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para ayudar a proteger los dispositivos administrados por Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b439067d06cf49a4ff83288e109d1fccd3801106
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722727"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integración de Jamf Pro con Intune para cumplimiento

Se aplica a: Intune en el portal de Azure

Si la organización usa [Jamf Pro](https://www.jamf.com) para administrar los equipos Mac de los usuarios finales, puede usar las directivas de cumplimiento de Microsoft Intune con acceso condicional de Azure Active Directory para garantizar que los dispositivos de la organización son compatibles.

## <a name="prerequisites"></a>Requisitos previos

Necesitará lo siguiente para configurar el acceso condicional con Jamf Pro:

- Jamf Pro 10.1.0 o versiones posteriores
- [Aplicación Portal de empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS con OS X 10.11 Yosemite o versiones posteriores

## <a name="connect-intune-to-jamf-pro"></a>Conexión de Intune a Jamf Pro

Para conectar Intune con Jamf Pro:

1. Cree una aplicación en Azure.
2. Habilite Intune para su integración con Jamf Pro.
3. Configure el acceso condicional en Jamf Pro.

## <a name="create-an-application-in-azure-active-directory"></a>Creación de una aplicación en Azure Active Directory

1. En [Azure Portal](https://portal.azure.com), vaya a **Azure Active Directory** > **Registros de aplicaciones** y seleccione **Nuevo registro**. 

2. En la página **Registrar una aplicación**, especifique estos detalles:
   - En la sección **Nombre**, escriba un nombre significativo para la aplicación, por ejemplo, **Acceso condicional de Jamf**.
   - Para la sección **Supported account types** (Tipos de cuenta admitidos), seleccione **Accounts in any organizational directory** (Cuentas en cualquier directorio organizativo). 
   - En **URI de redireccionamiento**, deje el valor predeterminado de Web y, luego, especifique la dirección URL de la instancia de Jamf Pro.  

3. Seleccione **Registrar** para crear la aplicación y abrir la página de **información general** de la aplicación nueva.  

4. En la página **Información general** de la aplicación, copie el valor de **Application (client) ID** (Identificador de aplicación [cliente]) y anótelo para usarlo más adelante. Lo necesitará en procedimientos posteriores.  

5. Seleccione **Certificates & secrets** (Certificados y secretos) en **Administrar**. Seleccione el botón **Nuevo secreto de cliente**. Escriba un valor en **Descripción**, seleccione cualquier opción para **Expira** y elija **Agregar**.

   > [!IMPORTANT]  
   > Antes de salir de la página, copie el valor del secreto de cliente y anótelo para usarlo más adelante. Lo necesitará en procedimientos posteriores. Este valor no vuelve a estar disponible sin volver a crear el registro de la aplicación.  

6. Seleccione **Permisos de API** en **Administrar**. Seleccione los permisos existentes y, luego, seleccione **Quitar permiso** para eliminar todos esos permisos. Quitar todos los permisos existentes es necesario, ya que agregará un nuevo permiso y la aplicación solo funciona si tiene un único permiso necesario.  

7. Para asignar un permiso nuevo, seleccione **Agregar un permiso**. En la página **Request API permissions** (Solicitar permisos de API), seleccione **Intune** y, luego, **Permisos de aplicación**. Active solo la casilla para **update_device_attributes**.  

   Seleccione **Agregar permiso** para guardar esta configuración.  

8. En la página **Permisos de API**, seleccione **Grant admin consent for Microsoft** (Conceder consentimiento del administrador para Microsoft) y, luego, seleccione **Sí**.  

   El proceso de registro de la aplicación en Azure AD se completó.


    > [!NOTE]
    > Si el secreto de cliente expira, debe crear otro secreto de cliente en Azure y luego actualizar los datos de acceso condicional en Jamf Pro. Azure permite tener activo tanto el secreto anterior como la clave nueva para evitar las interrupciones del servicio.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Habilitación de Intune para su integración con Jamf Pro

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) y vaya a **Microsoft Intune** > **Cumplimiento de dispositivos** > **Partner device management** (Administración de dispositivos de asociados).

2. Habilite el conector de cumplimiento para Jamf. Para ello, pegue el identificador de la aplicación que ha guardado en el procedimiento anterior en el campo **Jamf Azure Active Directory App ID** (Id. de aplicación de Azure Active Directory para Jamf).

3. Seleccione **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar la integración de Microsoft Intune en Jamf Pro

1. En Jamf Pro, navegue a **Administración global** > **Acceso condicional**. Haga clic en el botón **Editar** de la pestaña **macOS Intune Integration** (Integración de Intune para macOS).

2. Active la casilla **Enable Intune Integration for macOS** (Habilitar la integración de Intune para macOS).

3. Proporcione la información necesaria sobre su inquilino de Azure, como la **ubicación**, el **nombre de dominio**, el **identificador de aplicación** y el valor del *secreto de cliente* que guardó cuando creó la aplicación en Azure AD.  

4. Seleccione **Guardar**. Jamf Pro probará la configuración y confirmará que sea correcta.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurar directivas de cumplimiento y registrar dispositivos

Después de configurar la integración entre Intune y Jamf, tiene que [aplicar directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Desconexión de Jamf Pro e Intune 

Si ya no usa Jamf Pro para administrar los equipos Mac de la organización y desea que los usuarios se administren mediante Intune, debe quitar la conexión entre Jamf Pro e Intune. Quite la conexión mediante la consola de Jamf Pro. 

1. En Jamf Pro, vaya a **Administración global** > **Acceso condicional**. En la pestaña **Integración de MacOS Intune**, seleccione **Editar**.
2. Desactive la casilla **Enable Intune Integration for macOS** (Habilitar la integración de Intune para macOS).
3. Seleccione **Guardar**. Jamf Pro envía la configuración a Intune y se terminará la integración.
4. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Vaya a **Microsoft Intune** > **Device Compliance**  > **Partner device management** (Cumplimiento del dispositivo > Administración de dispositivos de asociados) para comprobar que el estado es ahora **Terminated** (Terminado). 

   > [!NOTE]
   > Los dispositivos Mac de la organización se retirarán en la fecha (tres meses) que se muestra en la consola. 

## <a name="next-steps"></a>Pasos siguientes

- [Aplicación de directivas de cumplimiento en los dispositivos administrados por Jamf](conditional-access-assign-jamf.md)
- [Datos que Jamf envía a Intune](data-jamf-sends-to-intune.md)
