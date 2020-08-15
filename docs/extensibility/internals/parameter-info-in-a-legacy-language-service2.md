---
title: Información de parámetros en un lenguaje heredado service2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dff6e871320d0727ed2fbec4188e8f7af2e5c5fe
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2020
ms.locfileid: "88237963"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Información de parámetros en un servicio de lenguaje heredado 2
La información de parámetros de IntelliSense es una información sobre herramientas que muestra la firma de un método cuando el usuario escribe el carácter de inicio de la lista de parámetros (normalmente un paréntesis de apertura) para la lista de parámetros de método. A medida que se escribe cada parámetro y se escribe el separador de parámetros (normalmente una coma), la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita.

 Las clases de Managed Package Framework (MPF) proporcionan compatibilidad para administrar la información de parámetros de la información sobre herramientas. El analizador debe detectar el inicio del parámetro, el parámetro siguiente y los caracteres finales del parámetro, y debe proporcionar una lista de las firmas de método y sus parámetros asociados.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información, vea [extender el editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="implementation"></a>Implementación
 El analizador debe establecer que el valor del desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> se establezca cuando encuentre un carácter de inicio de la lista de parámetros (a menudo un paréntesis de apertura). Debe establecer un <xref:Microsoft.VisualStudio.Package.TokenTriggers> desencadenador cuando encuentre un separador de parámetros (a menudo una coma). Esto hace que se actualice la información sobre herramientas de información de parámetros y muestre el siguiente parámetro en negrita. El analizador debe establecer el valor del desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> si encuentra el carácter final de la lista de parámetros (a menudo un paréntesis de cierre).

 El <xref:Microsoft.VisualStudio.Package.TokenTriggers> valor del desencadenador inicia una llamada al <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> método, que a su vez llama al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de métodos con un motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> . Si el analizador determina que el identificador antes del carácter de inicio de la lista de parámetros es un nombre de método reconocido, devuelve una lista de firmas de método coincidentes en el <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto. Si se encuentra alguna firma de método, se muestra la información sobre herramientas información de parámetros con la primera firma de la lista. Esta información sobre herramientas se actualiza a medida que se escribe más de la firma. Cuando se escribe el carácter final de la lista de parámetros, se quita la información sobre herramientas información de parámetros de la vista.

> [!NOTE]
> Para asegurarse de que la información sobre herramientas de información de parámetros está formateada correctamente, debe invalidar las propiedades en la <xref:Microsoft.VisualStudio.Package.Methods> clase para proporcionar los caracteres adecuados. La <xref:Microsoft.VisualStudio.Package.Methods> clase base asume una firma de método de estilo C#. Vea la <xref:Microsoft.VisualStudio.Package.Methods> clase para obtener más información sobre cómo se puede hacer esto.

## <a name="enabling-support-for-the-parameter-info"></a>Habilitar la compatibilidad con la información de parámetros
 Para admitir la información sobre herramientas de información de parámetros, debe establecer el `ShowCompletion` parámetro con nombre de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> en `true` . El servicio de lenguaje lee el valor de esta entrada del registro desde la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad.

 Además, la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> propiedad debe establecerse en `true` para que se muestre la información sobre herramientas de información de parámetros.

### <a name="example"></a>Ejemplo
 Este es un ejemplo simplificado de la detección de los caracteres de la lista de parámetros y de la configuración de los desencadenadores adecuados. Este ejemplo se utiliza únicamente con fines ilustrativos. Se supone que el escáner contiene un método `GetNextToken` que identifica y devuelve tokens de una línea de texto. El código de ejemplo simplemente establece los desencadenadores siempre que ve el tipo de carácter correcto.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Compatibilidad con la información sobre herramientas de información de parámetros en el analizador
 La <xref:Microsoft.VisualStudio.Package.Source> clase realiza algunas suposiciones sobre el contenido de las <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> clases y cuando se muestra y actualiza la información sobre herramientas de información de parámetros.

- El analizador se proporciona <xref:Microsoft.VisualStudio.Package.ParseReason> cuando se escribe el carácter de inicio de la lista de parámetros.

- La ubicación especificada en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto está inmediatamente después del carácter de inicio de la lista de parámetros. El analizador debe recopilar las firmas de todas las declaraciones de método disponibles en esa posición y almacenarlas en una lista en la versión del <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto. Esta lista incluye el nombre del método, el tipo de método (o el tipo de valor devuelto) y una lista de posibles parámetros. Posteriormente, se busca en esta lista las firmas o signaturas de método que se van a mostrar en la información sobre parámetros información sobre herramientas.

  A continuación, el analizador debe analizar la línea especificada por el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto para recopilar el nombre del método que se está escribiendo, así como la distancia entre el usuario y los parámetros de escritura. Para ello, se pasa el nombre del método al <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> método en el <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto y, a continuación, se llama al <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> método cuando se analiza el carácter de inicio de la lista de parámetros, se llama al <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> método cuando se analiza el carácter siguiente de la lista de parámetros y, por último, se llama al <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> método cuando se analiza el carácter final de la lista de parámetros. La clase utiliza los resultados de estas llamadas a métodos <xref:Microsoft.VisualStudio.Package.Source> para actualizar la información sobre herramientas de información de parámetros de forma adecuada.

### <a name="example"></a>Ejemplo
 Esta es una línea de texto que el usuario puede escribir. Los números que aparecen debajo de la línea indican qué paso toma el analizador en esa posición de la línea (suponiendo que el análisis se desplaza de izquierda a derecha). Aquí se supone que ya se ha analizado todo antes de la línea para las signaturas de método, incluida la firma del método "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Los pasos que realiza el analizador se describen a continuación:

1. El analizador llama a <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> con el texto "testfunc".

2. El analizador llama a <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. El analizador llama a <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. El analizador llama a <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
