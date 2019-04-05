---
title: Actualizar una extensión | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 321dca309476ecba80c0293f100ed64e7bb1cc4e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002604"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Filtrar Actualizar una extensión de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede actualizar una extensión de Visual Studio en el sistema mediante **extensiones y actualizaciones** para instalar la versión actualizada. Si crea una versión actualizada de una extensión, puede indicarla como actualizada al incrementar el número de versión en el manifiesto VSIX.

 Las actualizaciones se instalan al manifiesto de VSIX de la extensión de entrada tiene el mismo `ID` como lo instalado y una mayor `Version` número. Si el `Version` número es igual o inferior, no se puede instalar el paquete. Si el `ID` valores no coinciden, se reconoce el paquete que todavía no está instalado como una extensión independiente.

 Para evitar conflictos durante el desarrollo, se recomienda que desinstale las versiones anteriores de las extensiones en curso y también desinstalar o deshabilitar cualquier otra extensión potencialmente conflictiva.

### <a name="to-update-an-extension-on-your-system"></a>Para actualizar una extensión en el sistema

1.  En el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**

2.  En el panel izquierdo, haga clic en **actualizaciones**.

3.  En el panel central, haga clic en la actualización que desea instalar.

     El número de versión de la extensión actualizada se muestra en el panel derecho, junto con otra información.

4.  En la parte inferior del panel derecho, haga clic en **actualización**.

### <a name="to-publish-an-update-of-an-extension"></a>Para publicar una actualización de una extensión

1.  En Visual Studio, abra la solución para la extensión que desea actualizar. Realice los cambios.

    > [!IMPORTANT]
    >  Sin firmar que todas las extensiones de usuario no se actualizan automáticamente. Siempre debería firmar sus extensiones.

2.  En **el Explorador de soluciones**, abra source.extension.manifest.

3.  En el Diseñador de manifiestos, aumente el valor del número de la **versión** campo.

4.  Guarde la solución y genérelo.

5.  Cargue el nuevo archivo .vsix (en la carpeta \bin\Debug\ del proyecto) en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sitio Web.

     Cuando se abre un usuario que tenga una versión anterior de la extensión **extensiones y actualizaciones**, la nueva versión aparecerá en la **actualizaciones** enumerar, siempre que se establece la herramienta para buscar actualizaciones automáticamente.

     Puede habilitar o deshabilitar la comprobación automática de actualizaciones en la parte inferior de la **actualizaciones** panel (**habilitar o deshabilitar la detección automática de las actualizaciones disponibles**), los cambios que el **comprobar las actualizaciones** en **herramientas / opciones / entorno / extensiones y actualizaciones**.

    > [!NOTE]
    >  A partir de Visual Studio 2015 Update 2, puede especificar (en **Herramientas / Opciones / Entorno / Extensiones y actualizaciones**) si quiere actualizaciones automáticas para las extensiones por usuario, todas las extensiones de usuario o ambas (la configuración predeterminada).

## <a name="see-also"></a>Vea también
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md) [buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
