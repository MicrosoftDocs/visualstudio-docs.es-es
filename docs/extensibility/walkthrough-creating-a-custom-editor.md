---
title: 'Tutorial: Crear un Editor personalizado | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 74408fd88a594503c2a585cd0edfa86f28ed596e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-editor"></a>Tutorial: Crear un Editor personalizado
La plantilla de proyecto de VSPackage puede crear un editor personalizado simple en C++.  La plantilla de proyecto de VSPackage ya no admite proyectos de C# o Visual Basic. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>La plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto de paquete de Visual Studio puede encontrarse en el **nuevo proyecto** cuadro de diálogo de la carpeta de extensibilidad de C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Para crear un VSPackage mediante la plantilla de paquete de Visual Studio  
  
1.  Cree un proyecto con la plantilla de paquete de Visual Studio.  
  
2.  Seleccione el **Editor personalizado** opción y haga clic en **siguiente**. El **opciones del Editor de** se muestra la página.  
  
3.  Escriba el nombre de su editor en el **nombre de Editor** cuadro. Escriba la extensión de archivo que desea que estén asociados con el editor en el **extensión de archivo** cuadro. El editor está disponible para los archivos con esta extensión. La extensión de archivo está registrada para Visual Studio solo, no para Windows. Escriba el nombre de archivo predeterminado para documentos nuevos creados con el editor en el **nombre de archivo predeterminado** cuadro.  
  
4.  Haga clic en **Finalizar** para crear el VSPackage en la carpeta que especificó.  
  
### <a name="to-test-your-custom-editor"></a>Para probar el editor personalizado  
  
1.  En el **archivo** menú, elija **New** y, a continuación, haga clic en **archivo**.  
  
2.  En el **plantillas instaladas** panel de la **nuevo archivo** cuadro de diálogo, seleccione la plantilla de archivo y, a continuación, el archivo de tipo que acaba de registrar.  
  
3.  Haga clic en **abiertos** para ver y editar el documento.  
  
     El editor admite operaciones de cortar y pegar, buscar y reemplazar y abra y carga.  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)