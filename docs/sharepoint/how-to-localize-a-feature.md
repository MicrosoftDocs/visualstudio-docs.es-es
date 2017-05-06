---
title: "C&#243;mo: Localizar una caracter&#237;stica"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "características [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, adaptar"
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# C&#243;mo: Localizar una caracter&#237;stica
  De forma predeterminada, los títulos y descripciones de las características usan valores de cadena codificados de forma rígida.  Para localizar el título y la descripción de una característica, sustituya las cadenas por expresiones que hagan referencia a los recursos localizados.  
  
## Localizar una característica  
  
#### Para localizar una característica  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el nodo de **Característica1** y, a continuación **Agregue el recurso de características**.  
  
2.  En el cuadro de diálogo de **Agregar recurso** , elija **Idioma invariable** de la lista como referencia cultural del archivo de recursos de características de idioma predeterminado.  
  
3.  Repita el paso anterior para cada idioma adaptado, elija los lenguajes de la opción para los archivos de recursos de características.  
  
     Se crean los archivos de recursos de características independientes: uno para el idioma predeterminado y otro para cada idioma localizado que desee.  
  
4.  Abra cada archivo de recursos en el editor de recursos y, a continuación escribe todos los id. de la cadena y sus valores.  
  
     Por ejemplo, en el archivo de recursos de características predeterminado, especifique un identificador de cadena title con el valor de título de mi característica, y un segundo identificador de cadena de descripción con un valor de descripción de mi característica.  Para cada archivo de recursos localizado, utilice los mismos id. de la cadena utilizados en el recurso de características, pero especifique las cadenas localizadas para los valores.  
  
5.  Después de escribir todos los valores de recurso, abra el menú contextual para la característica \(por ejemplo, Feature1.feature\) y, a continuación **Diseñador de vistas** para abrir la característica en el diseñador de características.  
  
6.  Para buscar los campos de **title** y de **DESCRIPCIÓN** de la característica, utilice el siguiente formato para especificar valores en sus cuadros:  
  
     `$Resources:` *String ID*  
  
     Por ejemplo, escriba $Resources:Title en el cuadro **Título de la característica** y $Resources:Description en el cuadro **Descripción de la característica**.  
  
     Los id. de cadena deben coincidir con los que se usan en los archivos de recursos.  
  
7.  Elija la tecla F5 para compilar y ejecutar la aplicación.  
  
8.  En SharePoint, abra el menú de **Acciones del sitio** , elija **Configuración del sitio**y, a continuación, en la sección de **Acciones del sitio** elija el vínculo de **Administrar las características del sitio** .  
  
9. En SharePoint, cambie el idioma de presentación predeterminado.  
  
     El título y la descripción de la característica localizados aparecen en la aplicación.  Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.  
  
## Vea también  
 [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Cómo: Agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: Localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Cómo: Localizar código](../sharepoint/how-to-localize-code.md)  
  
  