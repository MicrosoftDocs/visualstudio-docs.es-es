---
title: 'Tutorial: crear un editor personalizado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b1b4e59e43a4a5aeb129464a34b96ef3f665e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148863"
---
# <a name="walkthrough-creating-a-custom-editor"></a>Tutorial: Creación de un editor personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La plantilla de proyecto VSPackage puede crear un editor personalizado simple en C++.  La plantilla de proyecto de VSPackage ya no es compatible con proyectos de C# o Visual Basic. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Prerrequisitos  
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>La plantilla de proyecto de paquete de Visual Studio  
 La plantilla de proyecto de paquete de Visual Studio se puede encontrar en el cuadro de diálogo **nuevo proyecto** de la carpeta de extensibilidad de C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Para crear un VSPackage mediante la plantilla de paquete de Visual Studio  
  
1. Cree un proyecto con la plantilla de paquete de Visual Studio.  
  
2. Seleccione la opción **editor personalizado** y haga clic en **siguiente**. Se muestra la página **Opciones del editor** .  
  
3. Escriba el nombre del editor en el cuadro **nombre del editor** . Escriba la extensión de archivo que desea asociar con el editor en el cuadro **extensión de archivo** . El editor está disponible para los archivos con esta extensión. La extensión de archivo está registrada solo para Visual Studio, no para Windows. Escriba el nombre de archivo predeterminado para los nuevos documentos creados con el editor en el cuadro **nombre de archivo predeterminado** .  
  
4. Haga clic en **Finalizar** para crear el VSPackage en la carpeta que especificó.  
  
### <a name="to-test-your-custom-editor"></a>Para probar el editor personalizado  
  
1. En el menú **archivo** , seleccione **nuevo** y haga clic en **archivo**.  
  
2. En el panel **plantillas instaladas** del cuadro de diálogo **nuevo archivo** , seleccione la plantilla de archivo y, a continuación, el tipo de archivo que acaba de registrar.  
  
3. Haga clic en **abrir** para ver y editar el documento.  
  
     El editor admite operaciones de cortar y pegar, buscar y reemplazar, y operaciones de apertura y carga.  
  
## <a name="see-also"></a>Consulte también  
 [VSPackages](../extensibility/internals/vspackages.md)
