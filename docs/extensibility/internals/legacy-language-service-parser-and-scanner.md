---
title: Analizador del servicio de lenguaje heredado y el analizador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8ed17e67246479772636d67bc8d9f218a3a3fc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333474"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Escáner y analizador del servicio de lenguaje heredado
El analizador es el corazón del servicio de lenguaje. Las clases de lenguaje de Managed Package Framework (MPF) requieren un analizador de lenguaje para seleccionar la información sobre el código que se va a mostrar. Un analizador separa el texto en tokens léxicos y, a continuación, identifica esos tokens por tipo y funcionalidad.

## <a name="discussion"></a>Discusión
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

 En este ejemplo, los tokens son las palabras y los signos de puntuación. Los tipos de tokens son como sigue.

|Nombre del token|Tipo de token|
|----------------|----------------|
|espacio de nombres, void público, de clase, int|palabra clave|
|=|operador|
|{ } ( ) ;|Delimitador|
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|
|MyNamespace|namespace|
|MyClass|clase|
|MyFunction|método|
|arg1|parámetro|
|var1|variable local|

 El rol del analizador es identificar los tokens. Algunos tokens pueden tener más de un tipo. Después de que el analizador ha identificado los tokens, el servicio de lenguaje puede usar la información para proporcionar características útiles, como resaltado de sintaxis, coincidencia de llaves y las operaciones de IntelliSense.

## <a name="types-of-parsers"></a>Tipos de analizadores
 Un analizador del servicio de lenguaje no es igual que un analizador que se usa como parte de un compilador. Sin embargo, este tipo de analizador debe usar un escáner y un analizador, en la misma manera que un analizador del compilador.

- Un escáner se usa para identificar los tipos de tokens. Esta información se usa para identificar rápidamente los tipos de token que pueden desencadenar otras operaciones, por ejemplo, coincidencia de llaves y resaltado de sintaxis. Este analizador se representa mediante el <xref:Microsoft.VisualStudio.Package.IScanner> interfaz.

- Un analizador se utiliza para describir las funciones y ámbito de los tokens. Esta información se utiliza en operaciones de IntelliSense para identificar los elementos del lenguaje, como métodos, variables, parámetros y las declaraciones y para proporcionar listas de miembros y las firmas de método en función del contexto. Este analizador también se utiliza para buscar pares coincidentes de elemento de lenguaje, como paréntesis y llaves. Este analizador se accede a través de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase.

  Cómo implementar un escáner y analizador para el servicio de lenguaje es decisión suya. Existen varios recursos que describen cómo funcionan los analizadores y cómo escribir su propio analizador. Además, existen varios productos gratuitos y comerciales que ayudan a crear un analizador.

### <a name="the-parsesource-parser"></a>El analizador ParseSource
 A diferencia de un analizador que se usa como parte de un compilador (donde los tokens se convierten en algún tipo de código ejecutable), se puede llamar un analizador del servicio de lenguaje por muchas razones diferentes y en muchos contextos diferentes. Cómo implementar este enfoque en el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase depende de usted. Es importante tener en cuenta que el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> es posible que se llama al método en un subproceso en segundo plano.

> [!CAUTION]
> El <xref:Microsoft.VisualStudio.Package.ParseRequest> estructura contiene una referencia a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto. Esto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto no se puede usar en el subproceso en segundo plano. De hecho, muchas de las clases MPF bases no se puede usar en el subproceso en segundo plano. Estos incluyen el <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> clases y cualquier otra clase que directa o indirectamente se comunica con la vista.

 Normalmente, este analizador analiza la hora del archivo el primer origen completo que se llame o cuando el análisis del valor de motivo <xref:Microsoft.VisualStudio.Package.ParseReason> se proporciona. Las llamadas posteriores a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método controlar una pequeña parte del código analizado y se pueden ejecutar mucho más rápidamente mediante el uso de los resultados de la operación de análisis completo anterior. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método comunica los resultados de la operación de análisis a través de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> y <xref:Microsoft.VisualStudio.Package.AuthoringScope> objetos. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se usa para recopilar información para un motivo concreto de análisis, por ejemplo, información sobre los intervalos de coincidencia de llaves o las firmas de método que tienen listas de parámetros. El <xref:Microsoft.VisualStudio.Package.AuthoringScope> proporciona colecciones de declaraciones y las firmas de método y también compatibilidad para ir a avanzada edición opción (**ir a definición**, **ir a declaración**, **vaya a Hacer referencia a**).

### <a name="the-iscanner-scanner"></a>El analizador IScanner
 También debe implementar un analizador que implementa <xref:Microsoft.VisualStudio.Package.IScanner>. Sin embargo, dado que este escáner funciona según una línea por línea a través de la <xref:Microsoft.VisualStudio.Package.Colorizer> (clase), es normalmente más fácil de implementar. Al principio de cada línea, MPF ofrece el <xref:Microsoft.VisualStudio.Package.Colorizer> un valor para utilizarlo como una variable de estado que se pasa al analizador de clases. Al final de cada línea, el analizador devuelve la variable de estado actualizada. MPF almacena esta información de estado para cada línea en la memoria caché para que pueda iniciar el analizador de análisis de cualquier línea sin tener que empezar al principio del archivo de origen. Este examen rápido de una sola línea permite que el editor proporcionar comentarios rápida al usuario.

## <a name="parsing-for-matching-braces"></a>Análisis de coincidencia de llaves
 En este ejemplo se muestra el flujo de control para la coincidencia de una llave de cierre que ha escrito por el usuario. En este proceso, el analizador que se usa para la coloración también se utiliza para determinar el tipo de token y si el token puede desencadenar una operación de coincidencia de llaves. Si se encuentra el desencadenador, la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se llama para buscar la llave correspondiente. Por último, se resaltan las dos llaves.

 Aunque las llaves se usan en los nombres de los desencadenadores y analizar las razones, este proceso no se limita a las llaves reales. Se admite cualquier par de caracteres que se especifica como una pareja coincidente. Algunos ejemplos son (y), \< y >, y [y].

 Se supone que el servicio de lenguaje es compatible con las llaves coincidentes.

1. El usuario escribe una llave de cierre (}).

2. La llave de cierre se inserta en la posición del cursor en el archivo de origen y avanza el cursor por uno.

3. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> clase se denomina con la llave de cierre con tipo.

4. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> clase para obtener el token en la posición justo antes de la posición actual del cursor. Este token se corresponde con la llave de cierre con tipo).

    1. El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método en el <xref:Microsoft.VisualStudio.Package.Colorizer> objeto para obtener todos los tokens en la línea actual.

    2. El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> llamadas al método el <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método en el <xref:Microsoft.VisualStudio.Package.IScanner> objeto con el texto de la línea actual.

    3. El <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método se llama repetidamente el <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método en el <xref:Microsoft.VisualStudio.Package.IScanner> objeto para recopilar todos los tokens de la línea actual.

    4. El <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método llama a un método privado el <xref:Microsoft.VisualStudio.Package.Source> clase para obtener el token que contiene la posición deseada y pasadas en la lista de los tokens obtienen de la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método.

5. El <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método busca un indicador de token de desencadenador de <xref:Microsoft.VisualStudio.Package.TokenTriggers> en el símbolo (token) que se devuelve desde el <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método; es decir, el token que representa la llave de cierre).

6. Si marca el desencadenador de <xref:Microsoft.VisualStudio.Package.TokenTriggers> se encuentra, el <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método en el <xref:Microsoft.VisualStudio.Package.Source> se llama a la clase.

7. El <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método inicia una operación de análisis con el valor de la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. Esta operación finalmente llama a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase. Si está habilitado el análisis asincrónico, esta llamada a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método se produce en un subproceso en segundo plano.

8. Cuando finalice la operación de análisis, un controlador de finalización interno (también conocido como un método de devolución de llamada) denominado `HandleMatchBracesResponse` se llama en el <xref:Microsoft.VisualStudio.Package.Source> clase. Esta llamada se realiza de forma automática el <xref:Microsoft.VisualStudio.Package.LanguageService> no por el analizador de la clase base.

9. El `HandleMatchBracesResponse` método obtiene una lista de intervalos desde el <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto que se almacena en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. (Un intervalo es un <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> estructura que especifica un intervalo de líneas y caracteres en el archivo de origen.) Esta lista de intervalos normalmente contiene dos intervalos, uno para la apertura y llaves de cierre.

10. El `HandleBracesResponse` llamadas al método el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto que se almacena en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. Esto resalta los intervalos dados.

11. Si el <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> está habilitada, el `HandleBracesResponse` método obtiene el texto que está incluido en el intervalo correspondiente y se muestra los primeros 80 caracteres de ese intervalo en la barra de estado. Esto funciona mejor si el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método incluye el elemento de lenguaje que acompaña a la par coincidente. Para obtener más información, vea la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Lleva a cabo.

### <a name="summary"></a>Resumen
 La operación de llaves coincidentes se suele limitarse a simple pares de elementos del lenguaje. Los elementos más complejos, como coincidencia triples ("`if(...)`","`{`"y"`}`", o "`else`","`{`"y"`}`"), puede aparecer resaltado como parte de una operación de finalización de palabras. Por ejemplo, cuando se termina la palabra "else", la coincidencia de "`if`" puede aparecer resaltada la instrucción. Si hubiera una serie de `if` / `else if` podrían resaltarse instrucciones, todos ellos usando el mismo mecanismo como coincidencia de llaves. La <xref:Microsoft.VisualStudio.Package.Source> clase base ya es compatible con esto, como sigue: El analizador debe devolver el valor del token de desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinado con el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> para el token que está antes de la posición del cursor.

 Para obtener más información, consulte [coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Análisis de coloración
 Coloreado de código fuente es sencilla, simplemente identifique el tipo de información de color de símbolo (token) y retorno sobre ese tipo. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase actúa como intermediario entre el editor y el analizador para proporcionar información de color sobre todos los tokens. El <xref:Microsoft.VisualStudio.Package.Colorizer> clase utiliza la <xref:Microsoft.VisualStudio.Package.IScanner> objeto para ayudar a colorear una línea y también para recopilar información de estado para todas las líneas del archivo de origen. En las clases de servicio de lenguaje MPF, el <xref:Microsoft.VisualStudio.Package.Colorizer> clase no tiene que reemplazarse porque se comunica con el escáner solo a través del <xref:Microsoft.VisualStudio.Package.IScanner> interfaz. Proporcione el objeto que implementa el <xref:Microsoft.VisualStudio.Package.IScanner> interfaz invalidando el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase.

 El <xref:Microsoft.VisualStudio.Package.IScanner> escáner se proporciona una línea de código fuente a través de la <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método. Las llamadas a la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método se repiten para obtener el token siguiente en la línea hasta que se agote la línea de tokens. Para la coloración, MPF trata todo el código fuente como una secuencia de líneas. Por lo tanto, el analizador debe ser capaz de hacer frente a llega a él como líneas de código fuente. Además, cualquier línea que puede pasarse al escáner en cualquier momento y la única garantía es que el analizador recibe la variable de estado de la línea antes de la línea que se va a analizar.

 La <xref:Microsoft.VisualStudio.Package.Colorizer> clase también se utiliza para identificar los desencadenadores de token. Estos desencadenadores indican MPF que un token concreto puede iniciar una operación más compleja, como la finalización de word o las llaves coincidentes. Dado que la identificación de estos desencadenadores debe ser rápido y debe producirse en cualquier ubicación, el analizador es más adecuado para esta tarea.

 Para obtener más información, consulte [coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Análisis de funcionalidad y ámbito
 Análisis de funcionalidad y ámbito requiere más esfuerzo que solo se identifican los tipos de tokens que se encuentran. El analizador debe identificar el tipo de token pero la funcionalidad para el que se usa el token. Por ejemplo, un identificador es simplemente un nombre, pero en su idioma, un identificador podría ser el nombre de una clase, espacio de nombres, método o variable, dependiendo del contexto. El tipo general del token puede ser un identificador, pero el identificador también puede tener otros significados, dependiendo de qué es y dónde está definido. Esta identificación requiere el analizador para tener más amplios conocimientos sobre el lenguaje que se está analizando. Aquí es donde el <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase entra en juego. El <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase recopila información acerca de identificadores, métodos, combinaciones de lenguas coincidentes (por ejemplo, paréntesis y llaves) y lenguaje triples (similar a los pares de idiomas, salvo que hay tres partes, por ejemplo, "`foreach()`" "`{`"y"`}`"). Además, puede invalidar el <xref:Microsoft.VisualStudio.Package.AuthoringSink> clase para admitir la identificación del código, que se utiliza en validación temprana de los puntos de interrupción para que el depurador no tiene que cargarse, y el **automático** ventana de depuración, que muestra local variables y parámetros automáticamente cuando un programa se está depurando y requiere que el analizador para identificar adecuadas variables locales y parámetros adicionales a los que se presenta el depurador.

 El <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto se pasa al analizador como parte de la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto y un nuevo <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto es crear cada vez que un nuevo <xref:Microsoft.VisualStudio.Package.ParseRequest> se crea el objeto. Además, el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método debe devolver un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto, que se usa para controlar varias operaciones de IntelliSense. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto mantiene una lista de declaraciones y una lista de métodos, ya sea de los cuales se rellena, dependiendo de la razón para el análisis. El <xref:Microsoft.VisualStudio.Package.AuthoringScope> se debe implementar la clase.

## <a name="see-also"></a>Vea también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Información general del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-overview.md)
- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)