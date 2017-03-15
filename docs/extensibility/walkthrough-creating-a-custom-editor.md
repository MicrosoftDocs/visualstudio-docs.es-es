---
title: "Tutorial: Crear un Editor personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creación editores [Visual Studio SDK] personalizados:"
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Tutorial: Crear un Editor personalizado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La plantilla de proyecto de VSPackage puede crear un editor personalizado simple en C\+\+.  La plantilla de proyecto de VSPackage ya no admite proyectos de C\# o Visual Basic. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## La plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto de paquete de Visual Studio puede encontrarse en el **nuevo proyecto** cuadro de diálogo en la carpeta de extensibilidad de C\+\+  
  
### Para crear un VSPackage utilizando la plantilla de paquete de Visual Studio  
  
1.  Cree un proyecto con la plantilla de paquete de Visual Studio.  
  
2.  Seleccione el **Editor personalizado** opción y haga clic en **siguiente**. El **Opciones del Editor de** se muestra la página.  
  
3.  Escriba el nombre del editor en el **nombre de Editor** cuadro. Escriba la extensión de archivo que desee que se asociará con el editor en el **extensión de archivo** cuadro. El editor está disponible para los archivos con esta extensión. La extensión de archivo está registrada para Visual Studio, no para Windows. Escriba el nombre de archivo predeterminado para nuevos documentos creados con el editor en el **nombre de archivo predeterminado** cuadro.  
  
4.  Haga clic en **Finalizar** para crear el VSPackage en la carpeta que especificó.  
  
### Para probar el editor personalizado  
  
1.  En el **archivo** menú, seleccione **nuevo** y, a continuación, haga clic en **archivo**.  
  
2.  En el **Plantillas instaladas** panel de la **nuevo archivo** cuadro de diálogo, seleccione la plantilla del archivo y, a continuación, el archivo de tipo al que se acaba de registrar.  
  
3.  Haga clic en **abiertos** para ver y editar el documento.  
  
     El editor admite operaciones de cortar y pegar, buscar y reemplazar y abrir y carga.  
  
## Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)