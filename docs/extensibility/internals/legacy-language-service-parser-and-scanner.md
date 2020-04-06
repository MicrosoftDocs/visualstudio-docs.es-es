---
title: Analizador y analizador del servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707313"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Escáner y analizador del servicio de lenguaje heredado
El analizador es el corazón del servicio de idiomas. Las clases de idioma de Managed Package Framework (MPF) requieren un analizador de idioma para seleccionar información sobre el código que se muestra. Un analizador separa el texto en tokens léxicos y, a continuación, identifica esos tokens por tipo y funcionalidad.

## <a name="discussion"></a>Discusión
 A continuación se muestra un método de C.

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

 En este ejemplo, los tokens son las palabras y los marcadores de puntuación. Los tipos de tokens son los siguientes.

|Nombre del token|Tipo de token|
|----------------|----------------|
|espacio de nombres, clase, público, vacío, int|palabra clave|
|=|operator|
|{ } ( ) ;|delimiter|
|MyNamespace, MyClass, MyFunction, arg1, var1|identificador|
|MyNamespace|espacio de nombres|
|MyClass|clase|
|MyFunction|method|
|arg1|parámetro|
|var1|variable local|

 El rol del analizador es identificar los tokens. Algunos tokens pueden tener más de un tipo. Una vez que el analizador ha identificado los tokens, el servicio de lenguaje puede usar la información para proporcionar características útiles, como resaltado de sintaxis, coincidencia de llaves y las operaciones de IntelliSense.

## <a name="types-of-parsers"></a>Tipos de analizadores
 Un analizador de servicio de lenguaje no es lo mismo que un analizador utilizado como parte de un compilador. Sin embargo, este tipo de analizador debe usar un analizador y un analizador, de la misma manera que un analizador del compilador.

- Un analizador se utiliza para identificar tipos de tokens. Esta información se usa para resaltar la sintaxis y para identificar rápidamente los tipos de token que pueden desencadenar otras operaciones, por ejemplo, la concordancia de llaves. Este escáner está representado <xref:Microsoft.VisualStudio.Package.IScanner> por la interfaz.

- Un analizador se utiliza para describir las funciones y el ámbito de los tokens. Esta información se utiliza en las operaciones de IntelliSense para identificar elementos de lenguaje, como métodos, variables, parámetros y declaraciones, y para proporcionar listas de miembros y firmas de método en función del contexto. Este analizador también se utiliza para localizar pares de elementos de lenguaje coincidentes, como llaves y paréntesis. Se accede a este <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador <xref:Microsoft.VisualStudio.Package.LanguageService> a través del método de la clase.

  La forma de implementar un analizador y un analizador para su servicio de lenguaje depende de usted. Hay varios recursos disponibles que describen cómo funcionan los analizadores y cómo escribir su propio analizador. Además, hay varios productos gratuitos y comerciales disponibles que ayudan a crear un analizador.

### <a name="the-parsesource-parser"></a>El analizador ParseSource
 A diferencia de un analizador que se usa como parte de un compilador (donde los tokens se convierten en alguna forma de código ejecutable), se puede llamar a un analizador de servicio de lenguaje por muchas razones diferentes y en muchos contextos diferentes. La forma de implementar <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> este <xref:Microsoft.VisualStudio.Package.LanguageService> enfoque en el método de la clase depende de usted. Es importante tener en cuenta <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> que se puede llamar al método en un subproceso en segundo plano.

> [!CAUTION]
> La <xref:Microsoft.VisualStudio.Package.ParseRequest> estructura contiene una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> referencia al objeto. Este <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto no se puede utilizar en el subproceso en segundo plano. De hecho, muchas de las clases MPF base no se pueden utilizar en el subproceso en segundo plano. Estas incluyen <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter>las <xref:Microsoft.VisualStudio.Package.CodeWindowManager> clases , , y cualquier otra clase que se comunique directa o indirectamente con la vista.

 Este analizador normalmente analiza todo el archivo de origen la primera vez <xref:Microsoft.VisualStudio.Package.ParseReason> que se llama o cuando se proporciona el valor de motivo de análisis. Las llamadas <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> posteriores al método controlan una pequeña parte del código analizado y se pueden ejecutar mucho más rápidamente mediante los resultados de la operación de análisis completo anterior. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método comunica los resultados de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> operación de análisis a través de los objetos y. <xref:Microsoft.VisualStudio.Package.AuthoringScope> El <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se utiliza para recopilar información para un motivo de análisis específico, por ejemplo, información sobre los intervalos de llaves coincidentes o firmas de método que tienen listas de parámetros. Proporciona <xref:Microsoft.VisualStudio.Package.AuthoringScope> colecciones de declaraciones y firmas de método y también compatibilidad con la opción de edición avanzada Ir**a (Ir a definición**, **Ir a declaración**, **Ir a referencia**).

### <a name="the-iscanner-scanner"></a>El escáner IScanner
 También debe implementar un analizador <xref:Microsoft.VisualStudio.Package.IScanner>que implemente . Sin embargo, dado que este analizador funciona línea <xref:Microsoft.VisualStudio.Package.Colorizer> por línea a través de la clase, normalmente es más fácil de implementar. Al principio de cada línea, el <xref:Microsoft.VisualStudio.Package.Colorizer> MPF proporciona a la clase un valor para utilizarlo como una variable de estado que se pasa al analizador. Al final de cada línea, el analizador devuelve la variable de estado actualizada. El MPF almacena en caché esta información de estado para cada línea para que el analizador pueda comenzar a analizar desde cualquier línea sin tener que iniciarse al principio del archivo de origen. Este escaneo rápido de una sola línea permite al editor proporcionar retroalimentación rápida al usuario.

## <a name="parsing-for-matching-braces"></a>Análisis de llaves a juego
 En este ejemplo se muestra el flujo de control para hacer coincidir una llave de cierre que el usuario ha escrito. En este proceso, el analizador que se utiliza para la coloración también se utiliza para determinar el tipo de token y si el token puede desencadenar una operación de coincidencia. Si se encuentra el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> desencadenador, se llama al método para buscar la llave coincidente. Por último, se resaltan las dos llaves.

 Aunque las llaves se utilizan en los nombres de desencadenadores y razones de análisis, este proceso no se limita a llaves reales. Se admite cualquier par de caracteres que se especifique que sea un par coincidente. Los ejemplos incluyen \< ( y ), y >, y [ y ].

 Supongamos que el servicio de lenguaje admite llaves coincidentes.

1. El usuario escribe una llave de cierre ( .

2. La llave se inserta en el cursor en el archivo de origen y el cursor se avanza por uno.

3. Se <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> llama <xref:Microsoft.VisualStudio.Package.Source> al método de la clase con la llave de cierre con tipo.

4. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> llama al <xref:Microsoft.VisualStudio.Package.Source> método de la clase para obtener el token en la posición justo antes de la posición actual del cursor. Este token corresponde a la llave de cierre con tipo).

    1. El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> llama al <xref:Microsoft.VisualStudio.Package.Colorizer> método en el objeto para obtener todos los tokens de la línea actual.

    2. El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> llama al <xref:Microsoft.VisualStudio.Package.IScanner> método en el objeto con el texto de la línea actual.

    3. El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método llama <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> repetidamente <xref:Microsoft.VisualStudio.Package.IScanner> al método en el objeto para recopilar todos los tokens de la línea actual.

    4. El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método llama a <xref:Microsoft.VisualStudio.Package.Source> un método privado en la clase para obtener el token que contiene <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> la posición deseada y pasa en la lista de tokens obtenidos del método.

5. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método busca una marca <xref:Microsoft.VisualStudio.Package.TokenTriggers> de desencadenador de token <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> en el token que se devuelve desde el método; es decir, el token que representa la llave de cierre).

6. Si se encuentra <xref:Microsoft.VisualStudio.Package.TokenTriggers> la marca <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> de <xref:Microsoft.VisualStudio.Package.Source> desencadenador de, se llama al método de la clase.

7. El <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método inicia una operación de análisis con el valor de motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. En última instancia, esta operación llama al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. Si el análisis asincrónico está <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> habilitado, esta llamada al método se produce en un subproceso en segundo plano.

8. Cuando finaliza la operación de análisis, se llama a un `HandleMatchBracesResponse` controlador de <xref:Microsoft.VisualStudio.Package.Source> finalización interno (también conocido como método de devolución de llamada) denominado en la clase. Esta llamada se realiza <xref:Microsoft.VisualStudio.Package.LanguageService> automáticamente por la clase base, no por el analizador.

9. El `HandleMatchBracesResponse` método obtiene una lista de <xref:Microsoft.VisualStudio.Package.AuthoringSink> intervalos del <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto que se almacena en el objeto. (Un intervalo <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> es una estructura que especifica un intervalo de líneas y caracteres en el archivo de origen.) Esta lista de intervalos normalmente contiene dos intervalos, uno para las llaves de apertura y cierre.

10. El `HandleBracesResponse` método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> método en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto que se almacena en el objeto. Esto resalta los intervalos dados.

11. Si <xref:Microsoft.VisualStudio.Package.LanguagePreferences> la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> propiedad está `HandleBracesResponse` habilitada, el método obtiene el texto que abarca el intervalo coincidente y muestra los primeros 80 caracteres de ese intervalo en la barra de estado. Esto funciona mejor <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> si el método incluye el elemento de lenguaje que acompaña al par coincidente. Para obtener más información, vea la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Listo.

### <a name="summary"></a>Resumen
 La operación de llaves coincidentes normalmente se limita a pares simples de elementos de lenguaje. Los elementos más complejos,`if(...)`como`{`los triples coincidentes (" ", "`}`" y " ", o ",`else`" "`{`y "`}`"), se pueden resaltar como parte de una operación de finalización de palabras. Por ejemplo, cuando finaliza la palabra "else", se puede resaltar la instrucción "`if`" " coincidente. Si hubiera una `if` / `else if` serie de instrucciones, todas ellas podrían resaltarse utilizando el mismo mecanismo que las llaves coincidentes. La <xref:Microsoft.VisualStudio.Package.Source> clase base ya admite esto, como se indica <xref:Microsoft.VisualStudio.Package.TokenTriggers> a continuación: <xref:Microsoft.VisualStudio.Package.TokenTriggers> el analizador debe devolver el valor del desencadenador de token combinado con el valor de desencadenador para el token que está antes de la posición del cursor.

 Para obtener más información, vea [Coincidencia de llaves en un servicio](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)de lenguaje heredado .

## <a name="parsing-for-colorization"></a>Análisis para la coloración
 Colorear el código fuente es sencillo, solo identifica el tipo de token y devuelve información de color sobre ese tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase actúa como intermediario entre el editor y el analizador para proporcionar información de color sobre cada token. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase <xref:Microsoft.VisualStudio.Package.IScanner> utiliza el objeto para ayudar a colorear una línea y también para recopilar información de estado para todas las líneas del archivo de origen. En las clases de <xref:Microsoft.VisualStudio.Package.Colorizer> servicio de lenguaje MPF, la clase no tiene <xref:Microsoft.VisualStudio.Package.IScanner> que ser reemplazada porque se comunica con el analizador sólo a través de la interfaz. Proporcione el objeto que <xref:Microsoft.VisualStudio.Package.IScanner> implementa la interfaz reemplazando el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.

 Al <xref:Microsoft.VisualStudio.Package.IScanner> analizador se le da una <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> línea de código fuente a través del método. Las llamadas al <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método se repiten para obtener el siguiente token en la línea hasta que se agote la línea de tokens. Para la coloración, el MPF trata todo el código fuente como una secuencia de líneas. Por lo tanto, el escáner debe ser capaz de hacer frente a la fuente que viene en él como líneas. Además, cualquier línea se puede pasar al escáner en cualquier momento, y la única garantía es que el escáner recibe la variable de estado de la línea antes de que la línea esté a punto de ser escaneada.

 La <xref:Microsoft.VisualStudio.Package.Colorizer> clase también se utiliza para identificar desencadenadores de token. Estos desencadenadores indican al MPF que un token determinado puede iniciar una operación más compleja, como la finalización de palabras o las llaves coincidentes. Dado que la identificación de estos desencadenadores debe ser rápida y debe producirse en cualquier ubicación, el escáner es el más adecuado para esta tarea.

 Para obtener más información, vea [Colorear sintaxis en un servicio](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)de lenguaje heredado .

## <a name="parsing-for-functionality-and-scope"></a>Análisis de funcionalidad y alcance
 El análisis de la funcionalidad y el ámbito requiere más esfuerzo que simplemente identificar los tipos de tokens que se encuentran. El analizador tiene que identificar no solo el tipo de token, sino también la funcionalidad para la que se utiliza el token. Por ejemplo, un identificador es solo un nombre, pero en su idioma, un identificador podría ser el nombre de una clase, espacio de nombres, método o variable, dependiendo del contexto. El tipo general del token puede ser un identificador, pero el identificador también puede tener otros significados, dependiendo de lo que es y dónde se define. Esta identificación requiere que el analizador tenga un conocimiento más amplio sobre el lenguaje que se está analizando. Aquí es <xref:Microsoft.VisualStudio.Package.AuthoringSink> donde entra en acción la clase. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase recopila información sobre identificadores, métodos, pares de idiomas coincidentes (como llaves y paréntesis) y triples`foreach()`de`{`lenguaje (similara a los pares de idiomas, excepto que hay tres partes, por ejemplo, " " " " y "`}`"). Además, puede <xref:Microsoft.VisualStudio.Package.AuthoringSink> invalidar la clase para admitir la identificación de código, que se utiliza en la validación temprana de puntos de interrupción para que no tenga que cargarse el depurador, y la ventana de depuración **Autos,** que muestra variables y parámetros locales automáticamente cuando se está depurando un programa y requiere que el analizador identifique las variables y parámetros locales adecuados además de los que presenta el depurador.

 El <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se pasa al analizador <xref:Microsoft.VisualStudio.Package.ParseRequest> como parte del <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto y se crea <xref:Microsoft.VisualStudio.Package.ParseRequest> un nuevo objeto cada vez que se crea un nuevo objeto. Además, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> el método <xref:Microsoft.VisualStudio.Package.AuthoringScope> debe devolver un objeto, que se utiliza para controlar varias operaciones de IntelliSense. El <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto mantiene una lista para las declaraciones y una lista para los métodos, cualquiera de los cuales se rellena, dependiendo del motivo del análisis. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase debe implementarse.

## <a name="see-also"></a>Vea también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)
- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
