---
title: '&lt;loc&gt; (JavaScript) | Documentos de Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ae2e4459a0da2dbcd096869cf49687c84a68b6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578545"
---
# <a name="ltlocgt-javascript"></a>&lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [documentación de Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Especifica la ubicación y el tipo de archivo asociado que proporciona información traducida de IntelliSense.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Opcional. Nombre raíz del archivo asociado que contiene información de localización para la referencia cultural neutra. Cuando Visual Studio busca información de localización, intenta encontrar una versión específica de la referencia cultural de este archivo. Por ejemplo, si `filename` es jquery.xml, Visual Studio busca la carpeta específica de la referencia cultural correcta (como JA) en la misma ubicación que el archivo .js que contiene el elemento `<loc>`. Si encuentra la carpeta específica de la referencia cultural, comprueba si existe un archivo jquery.xml en ella. Si no encuentra el archivo correcto, utiliza en su lugar reglas administradas de ubicación de recursos. El valor predeterminado para `filename` es el nombre del archivo actual, pero con una extensión .xml en lugar de .js.  
  
 `format`  
 Opcional. Tipo de archivo asociado utilizado para la localización. Utilice `messagebundle` para especificar el uso de paquetes de mensajes definidos por los metadatos de Open Ajax. El formato recomendado es `messagebundle`. Sin embargo, este formato no se admite en Microsoft Ajax ni en archivos .winmd. Utilice `vsdoc` para especificar el formato de localización estándar de .NET Framework utilizado por Microsoft Ajax y Windows en tiempo de ejecución. Este atributo es opcional. `vsdoc` es el formato predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 El elemento `<loc>` debe aparecer al principio del archivo, en la misma sección que el elemento `<reference>`. Las reglas de uso del elemento `<loc>` son iguales que las del elemento `<reference>`. Para obtener más información, vea la sección "Directivas Reference" en [IntelliSense para JavaScript](../ide/javascript-intellisense.md).  
  
 Visual Studio procesa un único elemento `<loc>` para cada archivo .js. Si hay varios elementos `<loc>` presentes, solo se utiliza un solo elemento `<loc>`. El comportamiento para determinar qué elemento `<loc>` se va a utilizar no está definido.  
  
 Cuando se utiliza el formato de paquete de mensajes, utilice el atributo `locid` en los comentarios de la documentación XML para especificar el valor del atributo `name`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el elemento `<loc>` con el formato messagebundle. Agregue el siguiente código XML a un archivo denominado messageFilename.xml y coloque el archivo en la carpeta específica de la referencia cultural correcta, como se especifica en la descripción del parámetro `filename`.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 En el ejemplo de messagebundle, agregue el código siguiente a un archivo JavaScript del proyecto. El elemento `<loc>` debe aparecer como la primera línea del archivo JavaScript. Las descripciones en este código se reemplazarán por descripciones traducidas, si están disponibles.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 En el ejemplo siguiente se utiliza el formato VSDoc. Agregue el código XML siguiente a un archivo denominado scriptFilename.xml y coloque el archivo en la carpeta específica de la referencia cultural correcta.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 En el ejemplo de VSDoc, agregue el código siguiente a un archivo JavaScript del proyecto. Las descripciones en este código se reemplazarán por descripciones traducidas, si están disponibles.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)



