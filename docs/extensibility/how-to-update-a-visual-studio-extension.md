---
title: "Cómo: actualizar una extensión de Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 46b540f1c5ba5b345464948170287d2b354b7a0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-a-visual-studio-extension"></a>Cómo: actualizar una extensión de Visual Studio
Puede actualizar una extensión de Visual Studio en el sistema mediante **extensiones y actualizaciones** para instalar la versión actualizada. Si crea una versión actualizada de una extensión, puede indicarla como actualizada incrementando el número de versión en el manifiesto VSIX.  
  
 Las actualizaciones se instalan cuando el manifiesto de VSIX de la extensión de entrada tiene el mismo `ID` como el instalado y un mayor `Version` número. Si el `Version` número es igual o inferior, no se puede instalar el paquete. Si el `ID` valores no coinciden, el paquete que todavía no está instalado se reconoce como una extensión independiente.  
  
 Para evitar conflictos durante el desarrollo, se recomienda desinstala las versiones anteriores de las extensiones en curso y también debe desinstala o deshabilita otras extensiones potencialmente conflictivas.  
  
### <a name="to-update-an-extension-on-your-system"></a>Para actualizar una extensión en el sistema  
  
1.  En el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**  
  
2.  En el panel izquierdo, haga clic en **actualizaciones**.  
  
3.  En el panel central, haga clic en la actualización que desea instalar.  
  
     El número de versión de la extensión actualizada se muestra en el panel derecho, junto con otra información.  
  
4.  En la parte inferior del panel derecho, haga clic en **actualización**.  
  
### <a name="to-publish-an-update-of-an-extension"></a>Para publicar una actualización de una extensión  
  
1.  En Visual Studio, abra la solución para la extensión que desea actualizar. Realice los cambios.  
  
    > [!IMPORTANT]
    >  Sin signo que todas las extensiones de usuario no se actualizan automáticamente. Siempre debería firmar sus extensiones.  
  
2.  En **el Explorador de soluciones**, abra source.extension.manifest.  
  
3.  En el Diseñador de manifiestos, aumente el valor del número de la **versión** campo.  
  
4.  Guarde la solución y genérelo.  
  
5.  Cargue el nuevo archivo .vsix (en la carpeta \bin\Debug\ del proyecto) en el [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sitio Web.  
  
     Cuando se abre un usuario que tenga una versión anterior de la extensión **extensiones y actualizaciones**, la nueva versión aparecerá en la **actualizaciones** enumerar, siempre que la herramienta se establece para que busque automáticamente las actualizaciones.  
  
     Puede habilitar o deshabilitar la comprobación automática de actualizaciones en la parte inferior de la **actualizaciones** panel (**habilitar/deshabilitar la detección automática de actualizaciones disponibles**), los cambios que el **buscar las actualizaciones de** en **herramientas / opciones / entorno / extensiones y actualizaciones**.  
  
    > [!NOTE]
    >  A partir de Visual Studio 2015 Update 2, puede especificar (en **Herramientas / Opciones / Entorno / Extensiones y actualizaciones**) si quiere actualizaciones automáticas para las extensiones por usuario, todas las extensiones de usuario o ambas (la configuración predeterminada).  
  
## <a name="see-also"></a>Vea también  
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
