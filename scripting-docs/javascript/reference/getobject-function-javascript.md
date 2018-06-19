---
title: GetObject (función) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637465"
---
# <a name="getobject-function-javascript"></a>GetObject (Función de JavaScript)
Devuelve una referencia a un objeto de automatización desde un archivo.  
  
> [!NOTE]
>  Esta función no se admite en Internet Explorer 9 (modo estándar) o una versión posterior.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>Parámetros  
 `pathname`  
 Opcional. Ruta de acceso completa y nombre del archivo que contiene el objeto que se va a recuperar. Si `pathname` se omite, `class` es necesario.  
  
 `class`  
 Opcional. Clase del objeto.  
  
 El `class` argumento utiliza la sintaxis `appname.objectype` y tiene las siguientes partes:  
  
 `appname`  
 Obligatorio. Nombre de la aplicación que proporciona el objeto.  
  
 `objectype`  
 Obligatorio. Tipo o clase de objeto a crear.  
  
## <a name="remarks"></a>Comentarios  
 El `GetObject` función no se admite en [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] o una versión posterior.  
  
 Use la `GetObject` función obtenga acceso a un objeto de automatización desde un archivo. Asigne el objeto devuelto por `GetObject` a la variable de objeto. Por ejemplo:  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Cuando se ejecuta este código, la aplicación asociada con los valores especificados `pathname` se inicia, y se activa el objeto en el archivo especificado. Si `pathname` es una cadena de longitud cero (""), `GetObject` devuelve una nueva instancia de objeto del tipo especificado. Si el `pathname` argumento se omite, `GetObject` devuelve un objeto activo del tipo especificado. Si no existe ningún objeto del tipo especificado, se produce un error.  
  
 Algunas aplicaciones permiten activar parte de un archivo. Para ello, agregue un signo de exclamación (!) al final del nombre de archivo y siga con una cadena que identifica la parte del archivo que desea activar. Para obtener información sobre cómo crear esta cadena, consulte la documentación de la aplicación que creó el objeto.  
  
 Por ejemplo, en una aplicación de dibujo podría tener varias capas para un dibujo almacenado en un archivo. Puede utilizar el código siguiente para activar una capa en un dibujo denominado `SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Si no especifica la clase del objeto, la automatización determina qué aplicación iniciar y qué objeto activar, tomando como base el nombre de archivo que proporcione. Sin embargo, algunos archivos, pueden admitir más de una clase de objeto. Por ejemplo, un dibujo podría admitir tres tipos diferentes de objetos: un objeto de aplicación, un objeto de dibujo y un objeto de barra de herramientas, que forman parte del mismo archivo. Para especificar qué objeto en un archivo que desea activar, use opcional `class` argumento. Por ejemplo:  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 En el ejemplo anterior, `FIGMENT` es el nombre de una aplicación de dibujo y `DRAWING` es uno de los tipos de objeto que admite. Una vez que un objeto se activa, hace referencia en código mediante la variable de objeto que ha definido. En el ejemplo anterior, accederás a propiedades y métodos del nuevo objeto mediante la variable de objeto `MyObject`. Por ejemplo:  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Use la `GetObject` funciona cuando hay una instancia del objeto actual, o si desea crear el objeto con un archivo cargado. Si no hay ninguna instancia actual y no desea iniciar el objeto con un archivo cargado, utilice la `ActiveXObject` objeto.  
  
 Si un objeto ha registrado como un objeto de instancia única, solo una instancia del objeto se crea, con independencia de cómo muchas veces `ActiveXObject` se ejecuta. Con un objeto de instancia única, `GetObject` siempre devuelve la misma instancia cuando se llama con la cadena de longitud cero ("") produce un error de sintaxis y, si la `pathname` argumento se omite.  
  
## <a name="requirements"></a>Requisitos  
 Admite los siguientes modos de documento: interpretación, estándar de Internet Explorer 6, Internet Explorer 7 y estándar de Internet Explorer 8. Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Vea también  
 [ActiveXObject (Objeto)](../../javascript/reference/activexobject-object-javascript.md)