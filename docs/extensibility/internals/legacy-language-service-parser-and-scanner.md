---
title: "Esc&#225;neres y analizador del servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analizadores, servicios de lenguaje [managed package framework]"
  - "Servicios de lenguaje [managed package framework], analizadores"
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Esc&#225;neres y analizador del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El analizador es el núcleo del servicio de lenguaje. Las clases de lenguaje administrado paquete Framework \(MPF\) requieren un analizador de lenguaje para seleccionar la información sobre el código que se muestra. Un analizador separa el texto en tokens léxicos e identifica esos tokens por tipo y funcionalidad.  
  
## Explicación  
 El siguiente es un método de C\#.  
  
```c#  
namespace MyNamespace { class MyClass { public void MyFunction(int arg1) { int var1 = arg1; } } }  
```  
  
 En este ejemplo, los tokens son las palabras y los signos de puntuación. Los tipos de símbolos \(tokens\) son los siguientes.  
  
|Nombre del token|Tipo de token|  
|----------------------|-------------------|  
|espacio de nombres, void público, de clase, int|palabra clave|  
|\=|operador|  
|{ } \( \) ;|delimitador|  
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|  
|MyNamespace|namespace|  
|MyClass|clase|  
|MyFunction|método|  
|Arg1|parámetro|  
|var1|variable local|  
  
 La función del analizador es identificar los tokens. Algunos tokens pueden tener más de un tipo. Después de que el analizador ha identificado los tokens, el servicio de lenguaje puede utilizar la información para proporcionar características útiles, como resaltado de sintaxis, coincidencia de llaves y las operaciones de IntelliSense.  
  
## Tipos de analizadores  
 Un analizador de servicio de lenguaje no es el mismo que un analizador que se utiliza como parte de un compilador. Sin embargo, este tipo de analizador deba utilizar un escáner y un analizador de la misma manera que un analizador de compilador.  
  
-   Un analizador se utiliza para identificar los tipos de símbolos \(tokens\). Esta información se usa para resaltar la sintaxis y para identificar rápidamente los tipos de token que se pueden desencadenar otras operaciones, por ejemplo, coincidencia de llaves. Este escáner está representado por la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz.  
  
-   Un analizador se utiliza para describir las funciones y el ámbito de los tokens. Esta información se utiliza en operaciones de IntelliSense para identificar los elementos de lenguaje, como métodos, variables, parámetros y declaraciones y para proporcionar listas de miembros y firmas de método basadas en contexto. Este analizador también se utiliza para buscar pares coincidentes de elemento de lenguaje, como paréntesis y llaves. Este analizador se tiene acceso mediante la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.  
  
 Cómo implementar un escáner y el analizador para el servicio de lenguaje es opcional. Existen varios recursos que describen el funcionamiento de los analizadores y cómo escribir su propio analizador. Además, existen varios productos gratuitos y comerciales que ayudan a crear un analizador.  
  
### El analizador ParseSource  
 A diferencia de un analizador que se utiliza como parte de un compilador \(donde los tokens se convierten en algún tipo de código ejecutable\), se puede llamar un analizador del servicio de lenguaje por muchas razones diferentes y en muchos contextos diferentes. Cómo implementar este enfoque en el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase depende de usted. Es importante tener en cuenta que el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método puede llamarse en un subproceso en segundo plano.  
  
> [!CAUTION]
>  El <xref:Microsoft.VisualStudio.Package.ParseRequest> estructura contiene una referencia a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto. Esto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> no se puede usar el objeto en el subproceso en segundo plano. De hecho, muchas de las clases bases de MPF no se utiliza en el subproceso en segundo plano. Entre ellos se incluyen la <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> clases y cualquier otra clase que directa o indirectamente, se comunica con la vista.  
  
 Normalmente, este analizador analiza la hora de la primera de archivo de origen completo se llama o cuando el análisis del motivo valor de <xref:Microsoft.VisualStudio.Package.ParseReason> se proporciona. Las llamadas posteriores a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método controlar una pequeña parte del código analizado y se pueden ejecutar mucho más rápidamente mediante el uso de los resultados de la operación de análisis completo anterior. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método comunica los resultados de la operación de análisis a través de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> y <xref:Microsoft.VisualStudio.Package.AuthoringScope> objetos. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se usa para recopilar información de un motivo específico de análisis, por ejemplo, información sobre los intervalos de llaves o firmas de método que tengan listas de parámetros. El <xref:Microsoft.VisualStudio.Package.AuthoringScope> proporciona colecciones de las declaraciones y las firmas de método y también soporte para ir a las avanzadas modificar opción \(**Ir a definición**, **Ir a declaración**, **Ir a referencia**\).  
  
### El analizador IScanner  
 También debe implementar un analizador que implementa <xref:Microsoft.VisualStudio.Package.IScanner>. Sin embargo, dado que este escáner funciona en forma de línea por línea a través de la <xref:Microsoft.VisualStudio.Package.Colorizer> \(clase\), es normalmente más fácil de implementar. Al principio de cada línea, le ofrece la MPF el <xref:Microsoft.VisualStudio.Package.Colorizer> un valor para utilizarlo como una variable de estado que se pasa al analizador de clase. Al final de cada línea, el analizador devuelve la variable de estado actualizada. La MPF almacena esta información de estado para cada línea para que pueda iniciar el analizador de análisis de cualquier línea sin tener que iniciar al principio del archivo de origen. Este examen rápido de una sola línea permite que el editor proporcionan comentarios rápidos al usuario.  
  
## Análisis de coincidencia de llaves  
 En este ejemplo se muestra el flujo de control para la coincidencia de una llave de cierre que ha escrito el usuario. En este proceso, el analizador que se utiliza para los colores también se utiliza para determinar el tipo de token y si el token puede desencadenar una operación de coincidencia de llaves. Si se encuentra el desencadenador, la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se llama para buscar la siguiente llave coincidente. Por último, se resaltan las dos llaves.  
  
 Aunque llaves se usan en los nombres de los desencadenadores y analizar los motivos, este proceso no se limita a las llaves reales. Se admite cualquier par de caracteres que se especifica como una coincidencia emparejar. Ejemplos \(y\), \< y \>, y \[y\].  
  
 Se supone que el servicio de lenguaje es compatible con las llaves.  
  
1.  El usuario escribe una llave de cierre \(}\).  
  
2.  La llave se inserta en la posición del cursor en el archivo de origen y avanza el cursor por uno.  
  
3.  El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase se denomina con la llave de cierre con tipo.  
  
4.  El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase para obtener el token en la posición justo antes de la posición actual del cursor. Este token se corresponde con la llave de cierre con tipo\).  
  
    1.  El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método en la <xref:Microsoft.VisualStudio.Package.Colorizer> objeto para obtener todos los tokens en la línea actual.  
  
    2.  El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método en la <xref:Microsoft.VisualStudio.Package.IScanner> objeto con el texto de la línea actual.  
  
    3.  El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método llama repetidamente el <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método en la <xref:Microsoft.VisualStudio.Package.IScanner> objeto para recopilar todos los tokens de la línea actual.  
  
    4.  El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método llama a un método privado la <xref:Microsoft.VisualStudio.Package.Source> clase para obtener el token que contiene la posición deseada y pasadas en la lista de símbolos \(tokens\) obtenido de la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> \(método\).  
  
5.  El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método busca una marca de símbolo \(token\) de desencadenador de <xref:Microsoft.VisualStudio.Package.TokenTriggers> en el token que se devuelve desde el <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método; es decir, el token que representa la llave de cierre\).  
  
6.  Si marca el desencadenador de <xref:Microsoft.VisualStudio.Package.TokenTriggers> se encuentra, el <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase se llama.  
  
7.  El <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método inicia una operación de análisis con el valor de la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. Esta operación finalmente llama el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. Si está habilitado el análisis asincrónico, esta llamada a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se produce en un subproceso en segundo plano.  
  
8.  Cuando finalice la operación de análisis, un controlador de finalización interno \(también conocido como un método de devolución de llamada\) denominado `HandleMatchBracesResponse` se llama el <xref:Microsoft.VisualStudio.Package.Source> clase. Esta llamada se realiza de forma automática el <xref:Microsoft.VisualStudio.Package.LanguageService> de la clase base no por el analizador.  
  
9. El `HandleMatchBracesResponse` método obtiene una lista de intervalos de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto almacenado en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. \(Una extensión es un <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> estructura que especifica un intervalo de líneas y caracteres en el archivo de origen.\) Esta lista de intervalos normalmente contiene dos intervalos, uno para la apertura y llaves de cierre.  
  
10. El `HandleBracesResponse` llamadas al método el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> método en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto almacenado en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. Esto resalta los intervalos determinados.  
  
11. Si el <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> está habilitada, el `HandleBracesResponse` método obtiene el texto que está incluido en el intervalo correspondiente y los primeros 80 caracteres de ese intervalo se muestra en la barra de estado. Esto funciona mejor si el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método incluye el elemento de lenguaje que acompaña a la par coincidente. Para obtener más información, vea la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Lleva a cabo.  
  
### Resumen  
 La operación de llaves coincidentes es típicamente limitada a simples pares de elementos de lenguaje. Los elementos más complejos, como la coincidencia de triples \("`if(…)`","`{`"y"`}`", o "`else`","`{`"y"`}`"\), se puede resaltar como parte de una operación de finalización de palabras. Por ejemplo, cuando se termina la palabra "else", la coincidencia de "`if`" se puede resaltar la instrucción. Si hay una serie de `if`\/`else if` podrían aparecer resaltadas instrucciones, todos ellos mediante el mismo mecanismo como coincidencia de llaves. La <xref:Microsoft.VisualStudio.Package.Source> clase base ya lo admite, como sigue: el analizador debe devolver el valor desencadenador token <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinado con el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> para el token antes de la posición del cursor.  
  
 Para obtener más información, consulta [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## Análisis de colores  
 Coloreado de código fuente es sencilla, simplemente identificar el tipo de token y devolución de información de color sobre dicho tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase actúa como intermediario entre el editor y el analizador para proporcionar información de color sobre cada token. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase utiliza la <xref:Microsoft.VisualStudio.Package.IScanner> objeto para ayudar a colorear una línea y para recopilar información de estado para todas las líneas del archivo de origen. En las clases de servicio de lenguaje MPF, la <xref:Microsoft.VisualStudio.Package.Colorizer> clase no tiene que reemplazarse porque se comunica con el escáner sólo mediante el <xref:Microsoft.VisualStudio.Package.IScanner> interfaz. Proporciona el objeto que implementa el <xref:Microsoft.VisualStudio.Package.IScanner> interfaz reemplazando el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.  
  
 El <xref:Microsoft.VisualStudio.Package.IScanner> Analizador tiene una línea de código fuente a través de la <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> \(método\). Las llamadas a la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método se repiten para obtener el token siguiente en la línea hasta que se agote la línea de tokens. Para los colores, la MPF trata todo el código fuente como una secuencia de líneas. Por lo tanto, el analizador debe poder hacer frente a entrante, como líneas de código fuente. Además, ninguna línea puede pasarse al analizador en cualquier momento y la única garantía es que el analizador recibe la variable de estado de la línea antes de la línea que se va a analizar.  
  
 La <xref:Microsoft.VisualStudio.Package.Colorizer> clase también se utiliza para identificar los desencadenadores de token. Estos desencadenadores indican la MPF que un token concreto puede iniciar una operación más compleja, como la finalización de word o llaves. Debe identificar esos desencadenadores debe ser rápido y debe producirse en cualquier ubicación, el analizador es más adecuado para esta tarea.  
  
 Para obtener más información, consulta [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## Análisis de funcionalidad y ámbito  
 Análisis de funcionalidad y ámbito requiere más esfuerzo que simplemente en identificar los tipos de símbolos que se encuentran. El analizador debe identificar el tipo de token pero la funcionalidad para la que se usa el token. Por ejemplo, un identificador es simplemente un nombre, pero en su idioma, un identificador podría ser el nombre de clase, espacio de nombres, método o variable, dependiendo del contexto. El tipo general del token puede ser un identificador, pero el identificador también tienen otros significados, dependiendo de qué es y dónde está definido. Esta identificación requiere tener más amplios conocimientos sobre el lenguaje que se está analizando el analizador. Aquí es donde el <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase entra en juego. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase recopila información acerca de los identificadores, métodos, pares coincidentes de idioma \(por ejemplo, paréntesis y llaves\) y lenguaje triples \(similar a pares de idiomas, salvo que hay tres partes, por ejemplo, "`foreach()`" "`{`"y"`}`"\). Además, puede invalidar la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase para admitir la identificación del código, que se utiliza en validación temprana de puntos de interrupción para que el depurador no tiene que cargarse, y el **automático** ventana de depuración, que muestra las variables locales y parámetros automáticamente cuando un programa se está depurando y requiere el analizador para identificar adecuadas variables locales y parámetros adicionales a los que se presenta el depurador.  
  
 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se pasa al analizador como parte de la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto y un nuevo <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto es crear cada vez que un nuevo <xref:Microsoft.VisualStudio.Package.ParseRequest> se crea el objeto. Además, el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método debe devolver un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto, que se utiliza para controlar varias operaciones de IntelliSense. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto mantiene una lista de declaraciones y una lista de métodos, ya sea que se rellena, dependiendo de la razón para el análisis. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase debe implementarse.  
  
## Vea también  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)   
 [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)