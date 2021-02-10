---
title: 'Cómo: actualizar una extensión de Visual Studio | Microsoft Docs'
description: Obtenga información sobre cómo actualizar una extensión de Visual Studio en el sistema mediante el uso de extensiones y actualizaciones para instalar la versión actualizada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a79944fbb558e3e7a5debcfc6a64fe4b75aeb0c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946844"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Cómo: actualizar una extensión de Visual Studio
Puede actualizar una extensión de Visual Studio en el sistema mediante el uso de **extensiones y actualizaciones** para instalar la versión actualizada. Si crea una versión actualizada de una extensión, puede indicarla como actualizada incrementando el número de versión en el manifiesto de VSIX.

 Las actualizaciones se instalan cuando el manifiesto VSIX de la extensión entrante tiene el mismo `ID` que el instalado y un `Version` número mayor. Si el `Version` número es igual o inferior, no se puede instalar el paquete. Si los `ID` valores no coinciden, el paquete que todavía no está instalado se reconoce como una extensión independiente.

 Para ayudar a evitar conflictos durante el desarrollo, se recomienda desinstalar las versiones anteriores de las extensiones en curso, así como desinstalar o deshabilitar cualquier otra extensión potencialmente conflictiva.

## <a name="to-update-an-extension-on-your-system"></a>Para actualizar una extensión en el sistema

1. En el menú **Herramientas**, haga clic en **Extensiones y actualizaciones**.

2. En el panel izquierdo, haga clic en **actualizaciones**.

3. En el panel central, haga clic en la actualización que desea instalar.

     El número de versión de la extensión actualizada se muestra en el panel derecho, junto con otra información.

4. En la parte inferior del panel derecho, haga clic en **Actualizar**.

## <a name="to-publish-an-update-of-an-extension"></a>Para publicar una actualización de una extensión

1. En Visual Studio, abra la solución para la extensión que desea actualizar. Realice los cambios.

    > [!IMPORTANT]
    > No se actualizan automáticamente todas las extensiones de usuario sin firmar. Siempre debe firmar las extensiones.

2. En **Explorador de soluciones**, Abra *source. Extension. manifest*.

3. En el diseñador de manifiestos, aumente el valor del número en el campo **versión** .

4. Guarde la solución y genérelo.

5. Cargue el nuevo archivo *. vsix* (en la carpeta * \bin\debug \* del proyecto) en el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) .

     Cuando un usuario que tenga una versión anterior de la extensión Abra **extensiones y actualizaciones**, la nueva versión aparecerá en la lista de **actualizaciones** , siempre que la herramienta esté configurada para buscar actualizaciones automáticamente.

     Puede habilitar o deshabilitar la comprobación automática de actualizaciones en la parte inferior del panel **actualizaciones** (**habilitar o deshabilitar la detección automática de actualizaciones disponibles**), que cambia la configuración de **Buscar actualizaciones** en **herramientas**  >  **Opciones**  >  **entorno**  >  **extensiones y actualizaciones**.

    > [!NOTE]
    > A partir de Visual Studio 2015 Update 2, puede especificar (en **herramientas**  >  **Opciones** de  >  **entorno**  >  **y actualizaciones**) Si quiere actualizaciones automáticas para las extensiones por usuario, todas las extensiones de usuario o ambas (la configuración predeterminada).

## <a name="see-also"></a>Vea también
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Búsqueda y uso de extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
