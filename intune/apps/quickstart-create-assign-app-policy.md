---
title: 'Inicio rápido: Crear y asignar una directiva de protección de aplicaciones'
titleSuffix: Microsoft Intune
description: En este tutorial de inicio rápido usará Microsoft Intune para crear y asignar una directiva de protección de aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2586fce0-5dca-4686-b9c4-791778838401
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8642672de048b88f709fef72d2027ec78c3b4327
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724638"
---
# <a name="quickstart-create-and-assign-an-app-protection-policy"></a>Inicio rápido: Creación y asignación de una directiva de protección de aplicaciones

En este tutorial de inicio rápido usará Intune para crear y asignar una directiva de protección de aplicaciones a una aplicación cliente en el dispositivo de un usuario final. Intune usa directivas de protección de aplicaciones para confirmar que sus aplicaciones cumplen los requisitos de protección de datos de su organización.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Requisitos previos

- Para llevar a cabo este tutorial de inicio rápido, deberá [crear un usuario](../fundamentals/quickstart-create-user.md), [crear un grupo](../fundamentals/quickstart-create-group.md), [inscribir un dispositivo](../quickstart-setup-auto-enrollment.md) y [agregar y asignar una aplicación](../quickstart-add-assign-app.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como [administrador global o administrador de servicios de Intune](../fundamentals/users-add.md#types-of-administrators). Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="create-an-app-protection-policy"></a>Crear directivas de protección de aplicaciones

Use los siguientes pasos para crear una directiva de protección de aplicaciones:

1. En [Intune](https://aka.ms/intuneportal), seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Crear directiva**. 
2. Escriba la siguiente información: 

    - **Nombre**: *Protección de contenido de Windows 10*
    - **Descripción**: *Los usuarios asociados a esta directiva no podrán cortar, copiar ni pegar contenido entre la aplicación asignada y otras aplicaciones no administradas en el dispositivo.*
    - **Plataforma**: *Windows 10*
    - **Estado de inscripción**: *Con inscripción*

3. Seleccione **Aplicaciones protegidas** para seleccionar las aplicaciones que deben cumplir esta directiva.
4. Haga clic en **Agregar aplicaciones**.
5. En **Aplicaciones recomendadas**, seleccione **Word Mobile**.
5. Haga clic en **Aceptar** > **Aceptar**. 
6. Seleccione **Valores obligatorios** para configurar la aplicación.
7. Haga clic en **Valores obligatorios** para establecer el modo de Windows Information Protection. Si selecciona esta opción, se impedirá que los datos de empresa salgan de la aplicación protegida.
8. Haga clic en **Aceptar** > **Crear**.

Ahora verá la directiva de protección de aplicaciones en Intune.

### <a name="assign-the-app-protection-policy"></a>Asignar la directiva de protección de aplicaciones

Una vez creada la directiva de protección de aplicaciones en Intune, puede asignarla a grupos. 

Use los siguientes pasos para asignar la directiva de protección de aplicaciones:

1. En [Intune](https://aka.ms/intuneportal), seleccione **Intune** > **Aplicaciones cliente** > **Directivas de protección de aplicaciones**. 
2. Seleccione la directiva de protección de aplicaciones que ha creado. En este tutorial de inicio rápido, la directiva es **Protección de contenido de Windows 10**.
3. Seleccione **Asignaciones**.
4. Haga clic en **Seleccionar grupos para incluir** en la pestaña **Incluir**.
5. Seleccione **Contoso Testers** (Evaluadores de Contoso) como el grupo que se va a incluir.
6. Haga clic en **Seleccionar** > **Guardar**. 

Ya ha asignado la directiva de protección de aplicaciones.

> [!NOTE]
> Las directivas de protección de aplicaciones solo se pueden aplicar a grupos que contienen usuarios, y no a grupos que contienen dispositivos.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial de inicio rápido ha creado y asignado una directiva de protección de aplicaciones. Los usuarios de la aplicación que tengan asignada esta directiva no podrán cortar, copiar ni pegar contenido entre la aplicación asignada y otras aplicaciones no administradas en el dispositivo. Este tipo de protección le permitirá proteger los datos de su organización. Para obtener más información sobre las directivas de protección de aplicaciones de Intune, consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Crear y asignar un rol personalizado](../fundamentals/create-custom-role.md)
