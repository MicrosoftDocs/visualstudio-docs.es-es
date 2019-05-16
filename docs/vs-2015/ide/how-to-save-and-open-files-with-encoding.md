---
title: Procedimiento Guardar y abrir archivos con codificación | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58c06c67daef727db91fa42c7ee8ce97ff183f38
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685454"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Procedimiento Guardar y abrir archivos con codificación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede guardar archivos con codificación de caracteres específicos para admitir lenguajes bidireccionales. Además puede especificar una codificación al abrir un archivo para que Visual Studio lo muestre correctamente.  
  
### <a name="to-save-a-file-with-encoding"></a>Para guardar un archivo con codificación  
  
1. En el menú **Archivo**, elija **Guardar archivo como** y luego haga clic en el botón desplegable situado junto al botón **Guardar**.  
  
     Se mostrará el cuadro de diálogo **Opciones avanzadas para guardar**.  
  
2. En **Codificación**, seleccione la codificación que quiere usar para el archivo.  
  
3. Opcionalmente, en **Fin de línea**, seleccione el formato de los caracteres de fin de línea.  
  
     Esta opción es útil si va a intercambiar el archivo con usuarios de otro sistema operativo.  
  
     Si quiere trabajar con un archivo que sabe que está codificado de una forma concreta, puede indicar a Visual Studio que use esa codificación al abrirlo. El método que use depende de si el archivo forma parte del proyecto.  
  
### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Para abrir un archivo codificado que forma parte de un proyecto  
  
1. En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo y elija **Abrir con**.  
  
2. En el cuadro de diálogo **Abrir con**, elija el editor con el que abrir el archivo.  
  
     La mayoría de los editores de Visual Studio, como el editor de formularios, detecta automáticamente la codificación y abre el archivo correctamente. Si elige un editor que permite seleccionar una codificación, se muestra el cuadro de diálogo **Codificación**.  
  
3. En el cuadro de diálogo **Codificación**, seleccione la codificación que debe usar el editor.  
  
### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Para abrir un archivo codificado que no forma parte de un proyecto  
  
1. En el menú **Archivo**, seleccione **Abrir**, **Archivo** o **Archivo de Web** y luego seleccione el archivo que quiere abrir.  
  
2. Haga clic en el botón desplegable situado junto al botón **Abrir** y elija **Abrir con**.  
  
3. Siga los pasos 2 y 3 del procedimiento anterior.  
  
## <a name="see-also"></a>Vea también  
 [Codificación y globalización de Windows Forms](https://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
