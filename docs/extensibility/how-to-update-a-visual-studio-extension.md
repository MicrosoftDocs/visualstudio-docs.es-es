---
title: 'Cómo: Actualizar una extensión de Visual Studio ( Visual Studio Extension) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710658"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Cómo: Actualizar una extensión de Visual Studio
Puede actualizar una extensión de Visual Studio en el sistema mediante **Extensiones y actualizaciones** para instalar la versión actualizada. Si crea una versión actualizada de una extensión, puede significarla como actualizada incrementando el número de versión en el manifiesto VSIX.

 Las actualizaciones se instalan cuando el manifiesto `ID` VSIX de la `Version` extensión entrante tiene el mismo que el instalado y un número mayor. Si `Version` el número es el mismo o menor, el paquete no se puede instalar. Si `ID` los valores no coinciden, el paquete que aún no está instalado se reconoce como una extensión independiente.

 Para ayudar a evitar conflictos durante el desarrollo, se recomienda desinstalar versiones anteriores de extensiones en curso y también desinstalar o deshabilitar cualquier otra extensión potencialmente conflictiva.

## <a name="to-update-an-extension-on-your-system"></a>Para actualizar una extensión en el sistema

1. En el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**

2. En el panel izquierdo, haga clic en **Actualizaciones**.

3. En el panel central, haga clic en la actualización que desea instalar.

     El número de versión de la extensión actualizada se muestra en el panel derecho, junto con otra información.

4. En la parte inferior del panel derecho, haga clic en **Actualizar**.

## <a name="to-publish-an-update-of-an-extension"></a>Para publicar una actualización de una extensión

1. En Visual Studio, abra la solución para la extensión que desea actualizar. Realice los cambios.

    > [!IMPORTANT]
    > Sin firmar, todas las extensiones de usuario no se actualizan automáticamente. Siempre debe firmar sus extensiones.

2. En **el Explorador de soluciones**, abra *source.extension.manifest*.

3. En el diseñador de manifiestos, aumente el valor del número en el campo **Versión.**

4. Guarde la solución y compílela.

5. Cargue el nuevo archivo *.vsix* (en\* la carpeta *-bin-Debug del proyecto) en el sitio Web de [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

     Cuando un usuario que tiene una versión anterior de la extensión abre **Extensiones y actualizaciones**, la nueva versión aparecerá en la lista **Actualizaciones,** siempre que la herramienta esté configurada para buscar actualizaciones automáticamente.

     Puede habilitar o deshabilitar la comprobación automática de actualizaciones en**Environment** > la parte inferior del panel **Actualizaciones** **(Habilitar/deshabilitar la detección automática de actualizaciones disponibles),** que cambia la configuración **Buscar actualizaciones** **en** > **Extensiones y actualizaciones**de entorno de**opciones** > de herramientas .

    > [!NOTE]
    > A partir de Visual Studio 2015 Update 2, puede especificar**Environment** >  **(en** > Extensiones de entorno**y actualizaciones**de entorno de**opciones** > de herramientas) si desea actualizaciones automáticas para extensiones por usuario, todas las extensiones de usuario o ambas (la configuración predeterminada).

## <a name="see-also"></a>Vea también
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
