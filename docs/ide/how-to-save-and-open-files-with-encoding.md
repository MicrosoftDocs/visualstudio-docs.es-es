---
title: "Cómo: Guardar y abrir archivos con codificación | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 83faa2ad32073c4133295953afa6259e88eee2d5
ms.contentlocale: es-es
ms.lasthandoff: 05/30/2017

---
# Cómo: Guardar y abrir archivos con codificación
<a id="how-to-save-and-open-files-with-encoding" class="xliff"></a>
Puede guardar archivos con codificación de caracteres específicos para admitir lenguajes bidireccionales. Además puede especificar una codificación al abrir un archivo para que Visual Studio lo muestre correctamente.  
  
### Para guardar un archivo con codificación
<a id="to-save-a-file-with-encoding" class="xliff"></a>  
  
1.  En el menú **Archivo**, elija **Guardar archivo como** y luego haga clic en el botón desplegable situado junto al botón **Guardar**.  
  
     Se mostrará el cuadro de diálogo **Opciones avanzadas para guardar**.  
  
2.  En **Codificación**, seleccione la codificación que quiere usar para el archivo.  
  
3.  Opcionalmente, en **Fin de línea**, seleccione el formato de los caracteres de fin de línea.  
  
     Esta opción es útil si va a intercambiar el archivo con usuarios de otro sistema operativo.  
  
     Si quiere trabajar con un archivo que sabe que está codificado de una forma concreta, puede indicar a Visual Studio que use esa codificación al abrirlo. El método que use depende de si el archivo forma parte del proyecto.  
  
### Para abrir un archivo codificado que forma parte de un proyecto
<a id="to-open-an-encoded-file-that-is-part-of-a-project" class="xliff"></a>  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo y elija **Abrir con**.  
  
2.  En el cuadro de diálogo **Abrir con**, elija el editor con el que abrir el archivo.  
  
     La mayoría de los editores de Visual Studio, como el editor de formularios, detecta automáticamente la codificación y abre el archivo correctamente. Si elige un editor que permite seleccionar una codificación, se muestra el cuadro de diálogo **Codificación**.  
  
3.  En el cuadro de diálogo **Codificación**, seleccione la codificación que debe usar el editor.  
  
### Para abrir un archivo codificado que no forma parte de un proyecto
<a id="to-open-an-encoded-file-that-is-not-part-of-a-project" class="xliff"></a>  
  
1.  En el menú **Archivo**, seleccione **Abrir**, **Archivo** o **Archivo de Web** y luego seleccione el archivo que quiere abrir.  
  
2.  Haga clic en el botón desplegable situado junto al botón **Abrir** y elija **Abrir con**.  
  
3.  Siga los pasos 2 y 3 del procedimiento anterior.  
  
## Vea también
<a id="see-also" class="xliff"></a>  
 [Codificación y globalización de Windows Forms](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
