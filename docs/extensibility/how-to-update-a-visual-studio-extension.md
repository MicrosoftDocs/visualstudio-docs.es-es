---
title: "C&#243;mo: actualizar una extensi&#243;n de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paquete de actualización"
  - "actualizar la extensión"
  - "nueva versión del paquete"
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: actualizar una extensi&#243;n de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede actualizar una extensión de Visual Studio en el sistema mediante **extensiones y actualizaciones** para instalar la versión actualizada. Si crea una versión actualizada de una extensión, puede indicarla como actualizada incrementando el número de versión en el manifiesto de VSIX.  
  
 Las actualizaciones se instalan cuando el manifiesto de VSIX de la extensión de entrada tiene el mismo `ID` como el instalados y una mayor `Version` número. Si el `Version` número es igual o inferior, no se puede instalar el paquete. Si el `ID` valores no coinciden, el paquete que todavía no está instalado se reconoce como una extensión independiente.  
  
 Para evitar conflictos durante el desarrollo, se recomienda que desinstale las versiones anteriores de las extensiones en curso y también desinstalar o deshabilitar cualquier otra extensión potencialmente conflictivas.  
  
### Para actualizar una extensión en el sistema  
  
1.  En el menú **Herramientas**, haga clic en **Extensiones y actualizaciones**  
  
2.  En el panel izquierdo, haga clic en **actualizaciones**.  
  
3.  En el panel central, haga clic en la actualización que desea instalar.  
  
     El número de versión de la extensión actualizada se muestra en el panel derecho, junto con otra información.  
  
4.  En la parte inferior del panel derecho, haga clic en **actualización**.  
  
### Para publicar una actualización de una extensión  
  
1.  En Visual Studio, abra la solución para la extensión que desea actualizar. Realice los cambios.  
  
    > [!IMPORTANT]
    >  Sin signo que todas las extensiones de usuario no se actualizan automáticamente. Siempre debe firmar sus extensiones.  
  
2.  En **el Explorador de soluciones**, abra source.extension.manifest.  
  
3.  En el Diseñador de manifiestos, aumente el valor del número en el **versión** campo.  
  
4.  Guarde la solución y compílela.  
  
5.  Cargue el nuevo archivo .vsix \(en la carpeta \\bin\\Debug\\ del proyecto\) en el [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web.  
  
     Cuando se abre un usuario que tenga una versión anterior de la extensión **extensiones y actualizaciones**, la nueva versión aparecerá en la **actualizaciones** enumerar, siempre que se establezca la herramienta para buscar automáticamente actualizaciones.  
  
     Puede habilitar o deshabilitar la comprobación automática de actualizaciones en la parte inferior de la **actualizaciones** panel \(**Habilitar o deshabilitar la detección automática de actualizaciones disponibles**\), los cambios que el **Buscar actualizaciones** en **Herramientas \/ Opciones \/ entorno \/ extensiones y actualizaciones**.  
  
    > [!NOTE]
    >  A partir de la actualización 2 de Visual Studio 2015, puede especificar \(en **Herramientas \/ Opciones \/ entorno \/ extensiones y actualizaciones**\) si desea que las actualizaciones automáticas para las extensiones por usuario, todas las extensiones de usuario o ambos \(configuración predeterminada\).  
  
## Vea también  
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)