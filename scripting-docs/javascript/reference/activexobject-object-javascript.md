---
title: "ActiveXObject (Objeto de JavaScript) | Microsoft Docs"
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
  - "ActiveXObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ActiveXObject (objeto)"
  - "objetos de automatización, objetos de ActiveXObject"
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# ActiveXObject (Objeto de JavaScript)
Habilita y devuelve una referencia a un objeto de automatización  
  
 Este objeto se usa solo para crear instancias de objetos de automatización y no tiene miembros.  
  
> [!WARNING]
>  El objeto es una extensión de Microsoft y se admite solo en Internet Explorer, no en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Sintaxis  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## Parámetros  
 `newObj`  
 Obligatorio.  Nombre de variable a la que se asigna `ActiveXObject`.  
  
 `servername`  
 Obligatorio.  Nombre de la aplicación que proporciona el objeto.  
  
 `typename`  
 Obligatorio.  Tipo o clase del objeto que se va a crear.  
  
 `location`  
 Opcional.  Nombre del servidor de red donde se va a crear el objeto.  
  
## Comentarios  
 Los servidores de automatización proporcionan al menos un tipo de objeto.  Por ejemplo, una aplicación de procesamiento de texto puede proporcionar un objeto de aplicación, un objeto de documento y un objeto de barra de herramientas.  
  
 Es posible que pueda identificar los valores de `servername.typename` en un equipo host en la clave del Registro `HKEY_CLASSES_ROOT`.  Por ejemplo, a continuación se muestran algunos ejemplos de valores que puede encontrar, dependiendo de los programas instalados:  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  Los objetos de ActiveX pueden presentar problemas de seguridad.  Para utilizar el `ActiveXObject`, puede que tenga ajustar la configuración de seguridad de Internet Explorer para la zona de seguridad pertinente.  Por ejemplo, para la zona de Intranet local, deberá cambiar una configuración personalizada a "Inicializar y generar scripts de los controles ActiveX no marcados como seguros".  
  
 Para identificar los miembros de un objeto de automatización y usarlos en el código, puede que tenga que utilizar un explorador de objetos COM, como el [Visor de objetos OLE y COM](http://msdn.microsoft.com/library/d0kh9f4c.aspx), si no hay documentación de referencia disponible para el objeto de automatización.  
  
 Para crear un objeto de automatización, asigne el nuevo `ActiveXObject` a una variable de objeto:  
  
```javascript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 Este código inicia la aplicación creando el objeto \(en este caso, una hoja de cálculo de Microsoft Excel\).  Una vez que se crea un objeto, haga referencia a él en el código mediante la variable de objeto que ha definido.  En el ejemplo siguiente, puede tener acceso a las propiedades y a los métodos del nuevo objeto mediante la variable de objeto `ExcelSheet` y otros objetos de Excel, incluidos el objeto Application y la colección ActiveSheet.Cells.  
  
```javascript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## Requisitos  
 Se admite en los siguientes modos de documento: no estándar, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9, estándar de Internet Explorer 10 y estándar de Internet Explorer 11.  No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Vea [Información de versiones](../../javascript/reference/javascript-version-information.md).  
  
> [!NOTE]
>  No se puede crear un `ActiveXObject` en un servidor remoto en [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] o posterior.  
  
## Vea también  
 [GetObject \(Función\)](../../javascript/reference/getobject-function-javascript.md)   
 [Aplicación de ejemplo de autenticación única mediante el uso de HTML5\/WCF](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)