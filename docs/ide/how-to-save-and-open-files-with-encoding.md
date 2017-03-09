---
title: "C&#243;mo: Guardar y abrir archivos con codificaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compatibilidad con idiomas bidireccionales, archivos codificados"
  - "codificación de archivos, lenguajes bidireccionales"
  - "archivos, encoding"
  - "Unicode, compatibilidad con idiomas bidireccionales"
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Guardar y abrir archivos con codificaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede guardar archivos con una codificación de caracteres específica para que admitan idiomas bidireccionales.  También puede especificar una codificación cuando abra un archivo para que Visual Studio muestre el archivo correctamente.  
  
### Para guardar un archivo con codificación  
  
1.  En el menú **Archivo**, elija **Guardar archivo como** y, a continuación, haga clic en el botón desplegable situado junto al botón **Guardar**.  
  
     Aparecerá el cuadro de diálogo **Opciones avanzadas para guardar**.  
  
2.  En **Codificación**, seleccione la codificación que desea utilizar para el archivo.  
  
3.  De manera opcional, en **Fin de línea**, seleccione el formato de los caracteres de fin de línea.  
  
     Esta opción es muy útil si piensa intercambiar el archivo con usuarios de un sistema operativo diferente.  
  
     Si desea trabajar con un archivo que sepa que está codificado de un modo específico, puede indicar a Visual Studio que utilice esa codificación cuando abra el archivo.  El método que utilice depende de si el archivo forma parte del proyecto.  
  
### Para abrir un archivo codificado que forme parte de un proyecto  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el archivo y elija **Abrir con**.  
  
2.  En el cuadro de diálogo **Abrir con**, elija el editor con el que desea abrir el archivo.  
  
     Muchos editores de Visual Studio, como el Editor de formularios, detectan automáticamente la codificación y abren el archivo correctamente.  Si elige un editor que permita elegir una codificación, se muestra el cuadro de diálogo **Codificación**.  
  
3.  En el cuadro de diálogo **Codificación**, seleccione la codificación que deba usar el editor.  
  
### Para abrir un archivo codificado que no forme parte de un proyecto  
  
1.  En el menú **Archivo**, elija **Abrir**, **Archivo** o **Archivo de Web** y seleccione el archivo que desea abrir.  
  
2.  Haga clic en el botón desplegable que aparece junto al botón **Abrir** y elija **Abrir con**.  
  
3.  Siga los pasos 2 y 3 del procedimiento anterior.  
  
## Vea también  
 [Encoding and Windows Forms Globalization](../Topic/Encoding%20and%20Windows%20Forms%20Globalization.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)