---
title: Analizador y analizador del servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre el analizador y el analizador del servicio de lenguaje heredado que seleccionan información sobre el código que se muestra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c57bd9f8b71f861fd5be4176211af6907b27e74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090842"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Escáner y analizador del servicio de lenguaje heredado
El analizador es el corazón del servicio de lenguaje. Las clases de lenguaje de Managed Package Framework (MPF) requieren un analizador de lenguaje para seleccionar información sobre el código que se muestra. Un analizador separa el texto en tokens léxicos y, a continuación, identifica esos tokens por tipo y funcionalidad.

## <a name="discussion"></a>Debate
 A continuación se encuentra un método de C#.

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

 En este ejemplo, los tokens son las palabras y los signos de puntuación. Los tipos de tokens son los siguientes.

|Nombre del token|Tipo de token|
|----------------|----------------|
|espacio de nombres, clase, público, void, int|palabra clave|
|=|operator|
|{ } ( ) ;|delimiter|
|MyNameSpace, MyClass, myFunction, arg1, Var1|identificador|
|MyNamespace|namespace|
|MyClass|clase|
|MyFunction|method|
|arg1|parámetro|
|Var1|variable local|

 El rol del analizador es identificar los tokens. Algunos tokens pueden tener más de un tipo. Una vez que el analizador ha identificado los tokens, el servicio de lenguaje puede utilizar la información para proporcionar características útiles, como el resaltado de sintaxis, la coincidencia de llaves y las operaciones de IntelliSense.

## <a name="types-of-parsers"></a>Tipos de analizadores
 Un analizador del servicio de lenguaje no es el mismo que el analizador que se usa como parte de un compilador. Sin embargo, este tipo de analizador necesita usar un escáner y un analizador, de la misma manera que un analizador de compilador.

- Un escáner se usa para identificar tipos de tokens. Esta información se usa para resaltar la sintaxis y para identificar rápidamente los tipos de token que pueden desencadenar otras operaciones, por ejemplo, la concordancia de llaves. Este escáner se representa mediante la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz.

- Un analizador se usa para describir las funciones y el ámbito de los tokens. Esta información se utiliza en las operaciones de IntelliSense para identificar elementos de lenguaje, como métodos, variables, parámetros y declaraciones, y para proporcionar listas de miembros y firmas de método basadas en el contexto. Este analizador también se utiliza para buscar pares de elementos de lenguaje coincidentes, como llaves y paréntesis. Se tiene acceso a este analizador a través del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.

  La forma de implementar un analizador y un analizador para su servicio de lenguaje depende de usted. Hay disponibles varios recursos que describen cómo funcionan los analizadores y cómo escribir su propio analizador. Además, hay disponibles varios productos gratuitos y comerciales que ayudan a crear un analizador.

### <a name="the-parsesource-parser"></a>El analizador de ParseSource
 A diferencia de un analizador que se usa como parte de un compilador (donde los tokens se convierten en algún tipo de código ejecutable), se puede llamar a un analizador del servicio de lenguaje por muchos motivos diferentes y en muchos contextos diferentes. La forma de implementar este enfoque en el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase depende de usted. Es importante tener en cuenta que se <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> puede llamar al método en un subproceso en segundo plano.

> [!CAUTION]
> La <xref:Microsoft.VisualStudio.Package.ParseRequest> estructura contiene una referencia al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto. Este <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto no se puede usar en el subproceso en segundo plano. De hecho, muchas de las clases MPF base no se pueden utilizar en el subproceso en segundo plano. Entre ellas se incluyen las <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter> clases,, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> y cualquier otra clase que se comunique directa o indirectamente con la vista.

 Normalmente, este analizador analiza todo el archivo de código fuente la primera vez que se llama o cuando se proporciona el valor del motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> . Las llamadas subsiguientes al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método controlan una pequeña parte del código analizado y se pueden ejecutar mucho más rápidamente mediante el uso de los resultados de la operación de análisis completo anterior. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método comunica los resultados de la operación de análisis a través de los <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> objetos y. El <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se usa para recopilar información de un motivo de análisis concreto, por ejemplo, información sobre los intervalos de llaves coincidentes o las firmas de método que tienen listas de parámetros. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Proporciona colecciones de declaraciones y firmas de método y también admite la opción ir a edición avanzada (**ir a definición**, **ir a declaración**, **ir a referencia**).

### <a name="the-iscanner-scanner"></a>El escáner IScanner
 También debe implementar un escáner que implemente <xref:Microsoft.VisualStudio.Package.IScanner> . Sin embargo, dado que este escáner funciona línea a línea a través de la <xref:Microsoft.VisualStudio.Package.Colorizer> clase, normalmente es más fácil de implementar. Al principio de cada línea, el MPF proporciona a la <xref:Microsoft.VisualStudio.Package.Colorizer> clase un valor que se va a usar como una variable de estado que se pasa al escáner. Al final de cada línea, el analizador devuelve la variable de estado actualizada. MPF almacena en caché esta información de estado para cada línea de modo que el analizador pueda empezar a analizar desde cualquier línea sin tener que empezar al principio del archivo de código fuente. Este examen rápido de una sola línea permite que el editor proporcione comentarios rápidos al usuario.

## <a name="parsing-for-matching-braces"></a>Análisis de llaves coincidentes
 Este ejemplo muestra el flujo de control para buscar coincidencias de una llave de cierre que el usuario ha escrito. En este proceso, el analizador que se usa para la coloración también se usa para determinar el tipo de token y si el token puede desencadenar una operación de coincidencia de llaves. Si se encuentra el desencadenador, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> se llama al método para encontrar la llave correspondiente. Por último, las dos llaves se resaltan.

 Aunque se usan llaves en los nombres de los desencadenadores y motivos de análisis, este proceso no se limita a las llaves reales. Se admiten los pares de caracteres que se especifican como pares coincidentes. Entre los ejemplos se incluyen (y), \< and > y [y].

 Supongamos que el servicio de lenguaje admite llaves coincidentes.

1. El usuario escribe una llave de cierre (}).

2. La llave se inserta en el cursor en el archivo de código fuente y el cursor está avanzado en uno.

3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Se llama al método de la <xref:Microsoft.VisualStudio.Package.Source> clase con la llave de cierre con tipo.

4. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método llama al <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método de la <xref:Microsoft.VisualStudio.Package.Source> clase para obtener el token en la posición inmediatamente anterior a la posición actual del cursor. Este token corresponde a la llave de cierre con tipo).

    1. El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método llama al <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método en el <xref:Microsoft.VisualStudio.Package.Colorizer> objeto para obtener todos los tokens en la línea actual.

    2. El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método llama al <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método en el <xref:Microsoft.VisualStudio.Package.IScanner> objeto con el texto de la línea actual.

    3. El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método llama repetidamente al <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método en el <xref:Microsoft.VisualStudio.Package.IScanner> objeto para recopilar todos los tokens de la línea actual.

    4. El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método llama a un método privado en la <xref:Microsoft.VisualStudio.Package.Source> clase para obtener el token que contiene la posición deseada y pasa la lista de tokens obtenida del <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método.

5. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método busca una marca de desencadenador de tokens de <xref:Microsoft.VisualStudio.Package.TokenTriggers> en el token que se devuelve del <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método; es decir, el token que representa la llave de cierre).

6. Si se encuentra la marca de desencadenador de <xref:Microsoft.VisualStudio.Package.TokenTriggers> , <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> se llama al método de la <xref:Microsoft.VisualStudio.Package.Source> clase.

7. El <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método inicia una operación de análisis con el valor del motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> . En última instancia, esta operación llama al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. Si el análisis asincrónico está habilitado, esta llamada al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se produce en un subproceso en segundo plano.

8. Cuando finaliza la operación de análisis, se llama a un controlador de finalización interno (también conocido como método de devolución de llamada) denominado `HandleMatchBracesResponse` en la <xref:Microsoft.VisualStudio.Package.Source> clase. Esta llamada la realiza automáticamente la <xref:Microsoft.VisualStudio.Package.LanguageService> clase base, no el analizador.

9. El `HandleMatchBracesResponse` método obtiene una lista de intervalos del <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto almacenado en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. (Un intervalo es una <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> estructura que especifica un intervalo de líneas y caracteres en el archivo de código fuente). Esta lista de intervalos normalmente contiene dos intervalos, uno para cada una de las llaves de apertura y cierre.

10. El `HandleBracesResponse` método llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto almacenado en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. Esto resalta los intervalos especificados.

11. Si la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> está habilitada, el `HandleBracesResponse` método obtiene el texto que está incluido en el intervalo de coincidencia y muestra los primeros 80 caracteres de ese intervalo en la barra de estado. Esto funciona mejor si el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método incluye el elemento de lenguaje que acompaña al par coincidente. Para obtener más información, vea la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Listo.

### <a name="summary"></a>Resumen
 La operación de llaves coincidentes se limita normalmente a pares simples de elementos del lenguaje. Los elementos más complejos, como los triples coincidentes (" `if(...)` ", " `{` " y " `}` ", o " `else` ", " `{` " y " `}` "), pueden resaltarse como parte de una operación de finalización de palabras. Por ejemplo, cuando finaliza la palabra "Else", se `if` puede resaltar la instrucción "" correspondiente. Si hubiera una serie de `if` / `else if` instrucciones, todas ellas podrían resaltarse con el mismo mecanismo que las llaves coincidentes. La <xref:Microsoft.VisualStudio.Package.Source> clase base ya es compatible con esto, como se indica a continuación: el escáner debe devolver el valor del desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> de token combinado con el valor del desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> para el token que está antes de la posición del cursor.

 Para obtener más información, consulte [coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Análisis de coloración
 La coloración del código fuente es sencilla, solo identifica el tipo de token y devuelve información de color sobre ese tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase actúa como intermediario entre el editor y el escáner para proporcionar información de color sobre cada token. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase utiliza el <xref:Microsoft.VisualStudio.Package.IScanner> objeto para ayudar a colorear una línea y también para recopilar información de estado para todas las líneas del archivo de código fuente. En las clases de servicio del lenguaje MPF, <xref:Microsoft.VisualStudio.Package.Colorizer> no es necesario invalidar la clase porque se comunica con el escáner solo a través de la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz. Proporcione el objeto que implementa la <xref:Microsoft.VisualStudio.Package.IScanner> interfaz invalidando el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.

 Al <xref:Microsoft.VisualStudio.Package.IScanner> escáner se le asigna una línea de código fuente a través del <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método. Las llamadas al <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método se repiten para obtener el siguiente token en la línea hasta que se agote la línea de los tokens. Para la coloración, el MPF trata todo el código fuente como una secuencia de líneas. Por lo tanto, el escáner debe ser capaz de hacer frente al origen que llega como líneas. Además, se puede pasar cualquier línea al escáner en cualquier momento y la única garantía es que el analizador recibe la variable de estado de la línea antes de la línea que se va a examinar.

 La <xref:Microsoft.VisualStudio.Package.Colorizer> clase también se utiliza para identificar los desencadenadores de token. Estos desencadenadores indican al MPF que un determinado token puede iniciar una operación más compleja, como la finalización de palabras o llaves coincidentes. Dado que la identificación de estos desencadenadores debe ser rápida y debe producirse en cualquier ubicación, el escáner es más adecuado para esta tarea.

 Para obtener más información, vea [coloración de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Análisis de funcionalidad y ámbito
 El análisis de la funcionalidad y el ámbito requiere más esfuerzo que identificar solo los tipos de tokens que se encuentran. El analizador tiene que identificar no solo el tipo de token, sino también la funcionalidad para la que se utiliza el token. Por ejemplo, un identificador es simplemente un nombre, pero en su lenguaje, un identificador podría ser el nombre de una clase, un espacio de nombres, un método o una variable, dependiendo del contexto. El tipo general del token puede ser un identificador, pero el identificador también puede tener otros significados, en función de qué es y dónde se define. Esta identificación requiere que el analizador tenga un conocimiento más profundo sobre el lenguaje que se está analizando. Aquí es donde <xref:Microsoft.VisualStudio.Package.AuthoringSink> entra en la clase. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase recopila información sobre los identificadores, métodos, pares de lenguajes coincidentes (como llaves y paréntesis) y tripas de lenguaje (similares a los pares de lenguajes, salvo que hay tres partes, por ejemplo, "" " `foreach()` `{` y" `}` "). Además, puede invalidar la <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase para admitir la identificación del código, que se usa en la validación temprana de puntos de interrupción para que no sea necesario cargar el depurador y la ventana de depuración **automática** , que muestra las variables locales y los parámetros automáticamente cuando se depura un programa y requiere que el analizador identifique las variables locales y los parámetros adecuados además de los que presenta el depurador

 El <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se pasa al analizador como parte del <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto y <xref:Microsoft.VisualStudio.Package.AuthoringSink> se crea un nuevo objeto cada vez que <xref:Microsoft.VisualStudio.Package.ParseRequest> se crea un nuevo objeto. Además, el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método debe devolver un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto, que se utiliza para controlar varias operaciones de IntelliSense. El <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto mantiene una lista para las declaraciones y una lista de los métodos, que se rellenan, en función del motivo del análisis. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Se debe implementar la clase.

## <a name="see-also"></a>Consulte también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)
- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
