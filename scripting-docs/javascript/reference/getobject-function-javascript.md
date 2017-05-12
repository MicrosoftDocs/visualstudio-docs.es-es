---
title: "GetObject (Funci&#243;n de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GetObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetObject (función)"
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# GetObject (Funci&#243;n de JavaScript)
Devuelve una referencia a un objeto de automatización desde un archivo.  
  
> [!NOTE]
>  Esta función no se admite en Internet Explorer 9 \(modo estándar\) o posterior.  
  
## Sintaxis  
  
```  
GetObject([pathname] [, class])  
```  
  
## Parámetros  
 `pathname`  
 Opcional.  Ruta completa y nombre del archivo que contiene el objeto que se va a recuperar.  Si se omite `pathname`, se requiere `class`.  
  
 `class`  
 Opcional.  Clase del objeto.  
  
 El argumento `class` usa la sintaxis `appname.objectype` y tiene estas partes:  
  
 `appname`  
 Requerido.  Nombre de la aplicación que proporciona el objeto.  
  
 `objectype`  
 Requerido.  Tipo o clase del objeto que se va a crear.  
  
## Comentarios  
 La función `GetObject` no se admite en [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] o posterior.  
  
 Use la función `GetObject` para tener acceso a un objeto de automatización desde un archivo.  Asigne el objeto devuelto por la función `GetObject` a la variable de objeto.  Por ejemplo:  
  
```javascript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Cuando se ejecuta este código, se inicia la aplicación asociada al argumento `pathname` especificado y se activa el objeto del archivo especificado.  Si `pathname` es una cadena de longitud cero \(""\), `GetObject` devuelve una nueva instancia de objeto del tipo especificado.  Si se omite el argumento `pathname`, `GetObject` devuelve un objeto actualmente activo del tipo especificado.  Si no existe ningún objeto del tipo especificado, se produce un error.  
  
 Algunas aplicaciones permiten activar parte de un archivo.  Para ello, agregue un signo de exclamación \(\!\) al final del nombre de archivo, seguido de una cadena que especifique la parte del archivo que desea activar.  Para obtener información sobre cómo crear esta cadena, consulte la documentación de la aplicación en la que se creó el objeto.  
  
 Por ejemplo, en una aplicación de dibujo, puede haber varias capas en un dibujo almacenado en un archivo.  Puede utilizar el código siguiente para activar una capa dentro de un dibujo denominado `SCHEMA.CAD`:  
  
```javascript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Si no especifica la clase del objeto, el objeto de automatización determina la aplicación que se va a iniciar y el objeto que se va a activar, basándose en el nombre de archivo que se proporcione.  Sin embargo, algunos archivos pueden admitir más de una clase de objeto.  Por ejemplo, un dibujo puede ser compatible con tres tipos diferentes de objetos: un objeto Application, un objeto Drawing y un objeto Toolbar, que forman parte todos ellos del mismo archivo.  Para especificar el objeto que desea activar en un archivo, utilice el argumento opcional `class`.  Por ejemplo:  
  
```javascript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 En el ejemplo anterior, `FIGMENT` es el nombre de una aplicación de dibujo y `DRAWING` es uno de los tipos de objeto que admite.  Una vez que se activa un objeto, se hace referencia a él en el código mediante la variable de objeto que haya definido.  En el ejemplo anterior, se tiene acceso a las propiedades y métodos del nuevo objeto mediante la variable de objeto `MyObject`.  Por ejemplo:  
  
```javascript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Utilice la función `GetObject` cuando exista una instancia actual del objeto o cuando desee crear el objeto con un archivo cargado.  Si no existe ninguna instancia actual y no desea que el objeto se inicie con un archivo cargado, utilice el objeto `ActiveXObject`.  
  
 Si un objeto se registró como objeto de una única instancia, sólo se creará una instancia del objeto, con independencia del número de veces que se ejecute el objeto `ActiveXObject`.  Con un objeto de una sola instancia, la función `GetObject` devuelve siempre la misma instancia cuando se llama con sintaxis de cadena de longitud cero \(""\) y origina un error si se omite el argumento `pathname`.  
  
## Requisitos  
 Se admite en los siguientes modos de documento: quirks \(modo de emulación de otros exploradores web\), estándar de Internet Explorer 6, estándar de Internet Explorer 7 y estándar de Internet Explorer 8.  Vea [Información de versiones](../../javascript/reference/javascript-version-information.md).  
  
## Vea también  
 [ActiveXObject \(Objeto\)](../../javascript/reference/activexobject-object-javascript.md)