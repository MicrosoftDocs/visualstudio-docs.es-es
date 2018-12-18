---
title: 'Cómo: actualizar una extensión de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8bf951215dfb4f6837c157a7b8510fba2d09f140
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500192"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Cómo: actualizar una extensión de Visual Studio
Puede actualizar una extensión de Visual Studio en el sistema mediante **extensiones y actualizaciones** para instalar la versión actualizada. Si crea una versión actualizada de una extensión, puede indicarla como actualizada al incrementar el número de versión en el manifiesto VSIX.  
  
 Las actualizaciones se instalan al manifiesto de VSIX de la extensión de entrada tiene el mismo `ID` como lo instalado y una mayor `Version` número. Si el `Version` número es igual o inferior, no se puede instalar el paquete. Si el `ID` valores no coinciden, se reconoce el paquete que todavía no está instalado como una extensión independiente.  
  
 Para evitar conflictos durante el desarrollo, se recomienda que desinstale las versiones anteriores de las extensiones en curso y también desinstalar o deshabilitar cualquier otra extensión potencialmente conflictiva.  
  
## <a name="to-update-an-extension-on-your-system"></a>Para actualizar una extensión en el sistema  
  
1.  En el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**  
  
2.  En el panel izquierdo, haga clic en **actualizaciones**.  
  
3.  En el panel central, haga clic en la actualización que desea instalar.  
  
     El número de versión de la extensión actualizada se muestra en el panel derecho, junto con otra información.  
  
4.  En la parte inferior del panel derecho, haga clic en **actualización**.  
  
## <a name="to-publish-an-update-of-an-extension"></a>Para publicar una actualización de una extensión  
  
1.  En Visual Studio, abra la solución para la extensión que desea actualizar. Realice los cambios.  
  
    > [!IMPORTANT]
    >  Sin firmar que todas las extensiones de usuario no se actualizan automáticamente. Siempre debería firmar sus extensiones.  
  
2.  En **el Explorador de soluciones**, abra *source.extension.manifest*.  
  
3.  En el Diseñador de manifiestos, aumente el valor del número de la **versión** campo.  
  
4.  Guarde la solución y genérelo.  
  
5.  Cargar el nuevo *.vsix* archivo (en el * \bin\Debug\* carpeta del proyecto) para el [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sitio Web.  
  
     Cuando se abre un usuario que tenga una versión anterior de la extensión **extensiones y actualizaciones**, la nueva versión aparecerá en la **actualizaciones** enumerar, siempre que se establece la herramienta para buscar actualizaciones automáticamente.  
  
     Puede habilitar o deshabilitar la comprobación automática de actualizaciones en la parte inferior de la **actualizaciones** panel (**habilitar o deshabilitar la detección automática de las actualizaciones disponibles**), los cambios que el **comprobar las actualizaciones** en **herramientas** > **opciones** > **entorno**  >  **Extensiones y actualizaciones**.  
  
    > [!NOTE]
    >  A partir de Visual Studio 2015 Update 2, puede especificar (en **herramientas** > **opciones** > **entorno**  >  **Extensiones y actualizaciones**) si desea que las actualizaciones automáticas para las extensiones por usuario, todas las extensiones de usuario o ambas (la configuración de la predeterminada).  
  
## <a name="see-also"></a>Vea también  
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)