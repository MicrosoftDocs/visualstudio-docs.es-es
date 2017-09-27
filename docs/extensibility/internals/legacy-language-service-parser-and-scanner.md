---
title: Analizador del servicio de lenguaje heredado y el analizador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c95dbbeaf9dcd6e1014ce3d2af8a0398c6627fe3
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="legacy-language-service-parser-and-scanner"></a>Escáneres y analizador del servicio de lenguaje heredado
El analizador es el núcleo del servicio de lenguaje. Las clases de lenguaje de Managed Package Framework (MPF) requieren un analizador de lenguaje para seleccionar la información sobre el código que se va a mostrar. Un analizador separa el texto en tokens léxicos y, a continuación, identifica esos tokens por tipo y funcionalidad.  
  
## <a name="discussion"></a>Explicación  
 El siguiente es un método de C#.  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 En este ejemplo, los tokens son las palabras y signos de puntuación. Los tipos de símbolos (tokens) son los siguientes.  
  
|Nombre del token|Tipo de token|  
|----------------|----------------|  
|espacio de nombres, void público, de clase, int|palabra clave|  
|=|operador|  
|{ } ( ) ;|Delimitador|  
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|  
|MyNamespace|namespace|  
|MyClass|clase|  
|MyFunction|método|  
|Arg1|parámetro|  
|var1|variable local|  
  
 El rol del analizador de XML consiste en identificar los tokens. Algunos tokens pueden tener más de un tipo. Después de que el analizador ha identificado los tokens, el servicio de lenguaje puede utilizar la información para proporcionar características útiles, como resaltado de sintaxis, coincidencia de llaves y las operaciones de IntelliSense.  
  
## <a name="types-of-parsers"></a>Tipos de analizadores  
 Un analizador del servicio de lenguaje no es igual que un analizador que se usa como parte de un compilador. Sin embargo, este tipo de analizador debe usar un escáner y un analizador, en la misma manera que un analizador de compilador.  
  
-   Un escáner se usa para identificar tipos de token. Esta información se usa para resaltar la sintaxis y para identificar rápidamente los tipos de token que pueden desencadenar otras operaciones, por ejemplo, coincidencia de llaves. Este analizador está representado por la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz.  
  
-   Un analizador se utiliza para describir las funciones y el ámbito de los tokens. Esta información se utiliza en operaciones de IntelliSense para identificar los elementos de lenguaje, como métodos, variables, parámetros y declaraciones y para proporcionar listas de miembros y las firmas de método basadas en contexto. Este analizador también se utiliza para buscar pares coincidentes de elemento de lenguaje, como paréntesis y llaves. Este analizador se accede a través del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.  
  
 Cómo implementar un escáner y el analizador para el servicio de lenguaje es depende de usted. Existen varios recursos que describen cómo funcionan los analizadores y cómo escribir su propio analizador. Además, existen varios productos gratuitos y comerciales que ayudan en la creación de un analizador.  
  
### <a name="the-parsesource-parser"></a>El analizador de ParseSource  
 A diferencia de un analizador que se utiliza como parte de un compilador (donde los tokens se convierten a algún formato de código ejecutable), un analizador del servicio de lenguaje puede llamarse por muchas razones diferentes y en muchos contextos diferentes. Cómo implementar este enfoque en el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase depende de usted. Es importante tener en cuenta que el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método puede llamarse en un subproceso en segundo plano.  
  
> [!CAUTION]
>  El <xref:Microsoft.VisualStudio.Package.ParseRequest> estructura contiene una referencia a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto. Esto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto no se puede usar en el subproceso en segundo plano. De hecho, muchas de las clases MPF base no se puede usar en el subproceso en segundo plano. Puede tratarse de la <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> clases y cualquier otra clase que directa o indirectamente, se comunica con la vista.  
  
 Este analizador normalmente analiza la hora de archivo del primer origen completo que se llame o cuando el análisis del motivo valor de <xref:Microsoft.VisualStudio.Package.ParseReason> recibe. Las llamadas posteriores a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método controlar una pequeña parte del código analizado y se puede ejecutar mucho más rápidamente mediante el uso de los resultados de la operación de análisis completo anterior. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método comunica los resultados de la operación de análisis a través de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> y <xref:Microsoft.VisualStudio.Package.AuthoringScope> objetos. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se usa para recopilar información para un motivo concreto de análisis, por ejemplo, información sobre los intervalos de coincidencia de llaves o las firmas de método que tengan listas de parámetros. El <xref:Microsoft.VisualStudio.Package.AuthoringScope> proporciona las colecciones de las declaraciones y las firmas de método y también compatibilidad para ir a avanzada edición opción (**ir a definición**, **ir a declaración**, **vaya a Hacer referencia a**).  
  
### <a name="the-iscanner-scanner"></a>El escáner IScanner  
 También debe implementar un escáner que implementa <xref:Microsoft.VisualStudio.Package.IScanner>. Sin embargo, dado que este escáner funciona en forma de línea por línea a través de la <xref:Microsoft.VisualStudio.Package.Colorizer> (clase), es normalmente más fácil de implementar. Al principio de cada línea, MPF ofrece la <xref:Microsoft.VisualStudio.Package.Colorizer> clase un valor para utilizarlo como una variable de estado que se pasa al escáner. Al final de cada línea, el analizador devuelve la variable de estado actualizada. MPF almacena esta información de estado para cada línea en la memoria caché para que el analizador puede iniciar el análisis de cualquiera de las líneas sin tener que iniciar al principio del archivo de origen. Este examen rápido de una sola línea permite que el editor proporcionar comentarios rápidos al usuario.  
  
## <a name="parsing-for-matching-braces"></a>Análisis de coincidencia de llaves  
 Este ejemplo muestra el flujo de control para la coincidencia de una llave de cierre que ha escrito el usuario. En este proceso, el analizador que se usa para coloración también se usa para determinar el tipo de símbolo (token) y si el token puede desencadenar una operación de coincidencia de llaves. Si se encuentra el desencadenador, la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se llama para buscar la llave correspondiente. Por último, se resaltan las dos llaves.  
  
 Aunque llaves se usan en los nombres de los desencadenadores y analizar motivos, este proceso no se limita a llaves reales. Se admite cualquier par de caracteres que se ha especificado como una coincidencia par. Algunos ejemplos son (y), \< y >, y [y].  
  
 Se supone que el servicio de lenguaje es compatible con llaves coincidentes.  
  
1.  El usuario escribe una llave de cierre (}).  
  
2.  La llave se inserta en la posición del cursor en el archivo de origen y el cursor avanza por uno.  
  
3.  El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase se denomina con la llave de cierre con tipo.  
  
4.  El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase para obtener el token en la posición justo antes de la posición actual del cursor. Este token se corresponde con la llave de cierre con tipo).  
  
    1.  El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método en la <xref:Microsoft.VisualStudio.Package.Colorizer> objeto para obtener todos los tokens de la línea actual.  
  
    2.  El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método en la <xref:Microsoft.VisualStudio.Package.IScanner> objeto con el texto de la línea actual.  
  
    3.  El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método llama repetidamente el <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método en la <xref:Microsoft.VisualStudio.Package.IScanner> objeto para recopilar todos los tokens de la línea actual.  
  
    4.  El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método llama a un método privado de la <xref:Microsoft.VisualStudio.Package.Source> clase para obtener el token que contiene la posición deseada y pasadas en la lista de símbolos (tokens) obtienen de la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método.  
  
5.  El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método busca un indicador de bits desencadenador token <xref:Microsoft.VisualStudio.Package.TokenTriggers> en el símbolo (token) que se devuelve desde el <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método; es decir, el token que representa la llave de cierre).  
  
6.  Si marca el desencadenador de <xref:Microsoft.VisualStudio.Package.TokenTriggers> se encuentra, el <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase se denomina.  
  
7.  El <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método inicia una operación de análisis con el valor de la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. Esta operación finalmente llama el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. Si está habilitado el análisis asincrónico, esta llamada a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se produce en un subproceso en segundo plano.  
  
8.  Cuando finalice la operación de análisis, un controlador de finalización interno (también conocido como un método de devolución de llamada) denominado `HandleMatchBracesResponse` se llama el <xref:Microsoft.VisualStudio.Package.Source> clase. Esta llamada se realiza de forma automática el <xref:Microsoft.VisualStudio.Package.LanguageService> de la clase base no por el analizador.  
  
9. El `HandleMatchBracesResponse` método obtiene una lista de intervalos de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto que se almacena en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. (Un intervalo es un <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> estructura que especifica un intervalo de líneas y caracteres en el archivo de origen.) Esta lista de intervalos de normalmente contiene dos intervalos, uno para la apertura y llaves de cierre.  
  
10. El `HandleBracesResponse` llamadas al método el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto que se almacena en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. Esto resalta los intervalos determinados.  
  
11. Si el <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> está habilitada, el `HandleBracesResponse` método obtiene el texto que está incluido en el intervalo de búsqueda de coincidencias y muestra los primeros 80 caracteres de ese intervalo en la barra de estado. Esto funciona mejor si la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método incluye el elemento de lenguaje que acompaña a la pareja coincidente. Para obtener más información, vea la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Lleva a cabo.  
  
### <a name="summary"></a>Resumen  
 La operación de llaves coincidentes se suelen limitar a simples pares de elementos de lenguaje. Elementos más complejos, como la coincidencia de triples ("`if(...)`","`{`"y"`}`", o "`else`","`{`"y"`}`"), puede resaltar como parte de una operación de finalización automática de palabras. Por ejemplo, cuando se termina la palabra "else", la coincidencia de "`if`" instrucción puede aparecer resaltada. Si hubiera una serie de `if` / `else if` instrucciones, todos ellos podrían resaltarse mediante el mismo mecanismo como llaves coincidentes. El <xref:Microsoft.VisualStudio.Package.Source> clase base ya es compatible con esto, como se indica a continuación: el escáner debe devolver el valor desencadenador token <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinado con el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> para el token que está antes de la posición del cursor.  
  
 Para obtener más información, consulte [la coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Análisis de colores  
 Coloreado de código fuente es sencillo, simplemente identifique el tipo de información de color de símbolo (token) y retorno sobre ese tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase actúa como intermediario entre el editor y el escáner para proporcionar información de color sobre cada símbolo (token). El <xref:Microsoft.VisualStudio.Package.Colorizer> clase utiliza la <xref:Microsoft.VisualStudio.Package.IScanner> objeto para ayudar a colorear una línea y también para recopilar información de estado para todas las líneas en el archivo de origen. En las clases de servicio de lenguaje MPF, el <xref:Microsoft.VisualStudio.Package.Colorizer> clase no tiene que reemplazarse porque se comunica con el escáner solo mediante la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz. Proporcionar el objeto que implementa el <xref:Microsoft.VisualStudio.Package.IScanner> interfaz reemplazando el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.  
  
 El <xref:Microsoft.VisualStudio.Package.IScanner> escáner tiene una línea de código fuente a través de la <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método. Llamadas a la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método se repiten para obtener el token siguiente en la línea hasta que se agote la línea de símbolos (tokens). Para los colores, MPF trata todo el código fuente como una secuencia de líneas. Por lo tanto, el analizador debe tener hacer frente a los que entran en él como líneas de código fuente. Además, cualquier línea puede pasarse al escáner en cualquier momento y la única garantía es que el escáner recibe la variable de estado de la línea antes de la línea que se va a analizar.  
  
 La <xref:Microsoft.VisualStudio.Package.Colorizer> clase también se utiliza para identificar los desencadenadores de símbolo (token). Estos desencadenadores indicarán MPF que un token determinado puede iniciar una operación más compleja, como la finalización de palabras o llaves coincidentes. Dado que identificar estos desencadenadores debe ser rápido y se debe producir en cualquier ubicación, el analizador es más apropiado para esta tarea.  
  
 Para obtener más información, consulte [coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Análisis de funcionalidad y ámbito  
 Análisis de funcionalidad y ámbito requiere más esfuerzo que simplemente identifica los tipos de tokens que se encuentran. El analizador debe identificar el tipo de token pero la funcionalidad para la que se usa el token. Por ejemplo, un identificador es simplemente un nombre, pero en su idioma, un identificador podría ser el nombre de clase, espacio de nombres, método o variable, en función del contexto. El tipo general del token puede ser un identificador, pero el identificador también puede tener otros significados, dependiendo de lo que es y donde se define. Esta identificación requiere el analizador que más amplios conocimientos sobre el lenguaje que se está analizando. Aquí es donde el <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase entra en juego. El <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase recopila información acerca de los identificadores, métodos, pares coincidentes de idioma (por ejemplo, paréntesis y llaves) y lenguaje triples (similar a pares de idioma, excepto en que hay tres partes, por ejemplo, "`foreach()`" "`{`"y"`}`"). Además, puede invalidar la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase para admitir la identificación de código, que se utiliza en la validación inicial de los puntos de interrupción para que el depurador no tiene que se va a cargar, y el **automático** ventana de depuración, que se muestra en local variables y parámetros automáticamente cuando un programa se está depurando y requiere que el analizador para identificar adecuadas variables locales y parámetros adicionales a los que se presenta el depurador.  
  
 El <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se pasa al analizador como parte de la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto y una nueva <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto es crear cada vez que un nuevo <xref:Microsoft.VisualStudio.Package.ParseRequest> se crea el objeto. Además, el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método debe devolver un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto, que se utiliza para controlar varias operaciones de IntelliSense. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto mantiene una lista de las declaraciones y una lista de métodos, ya sea de los cuales se rellena, dependiendo de la razón para el análisis. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase debe implementarse.  
  
## <a name="see-also"></a>Vea también  
 [Implementar un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Introducción al servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)   
 [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
