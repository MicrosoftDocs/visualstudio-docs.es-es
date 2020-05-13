---
title: Información de parámetros en un servicio de lenguaje heredado2 Microsoft Docs
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
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706747"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Información de parámetros en un servicio de lenguaje heredado
Información de parámetros de IntelliSense es una información sobre herramientas que muestra la firma de un método cuando el usuario escribe el carácter de inicio de la lista de parámetros (normalmente un paréntesis abierto) para la lista de parámetros de método. A medida que se introduce cada parámetro y se escribe el separador de parámetros (normalmente una coma), la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita.

 Las clases de marco de trabajo de paquete administrado (MPF) proporcionan compatibilidad para administrar la información sobre parámetros. El analizador debe detectar caracteres de inicio, siguiente y final de parámetro de parámetro, y debe proporcionar una lista de las firmas del método y sus parámetros asociados.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Ampliación del editor y](../../extensibility/extending-the-editor-and-language-services.md)los servicios de lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="implementation"></a>Implementación
 El analizador debe establecer <xref:Microsoft.VisualStudio.Package.TokenTriggers> el valor del desencadenador se establece cuando encuentra un carácter de inicio de lista de parámetros (a menudo un paréntesis abierto). Debe establecer <xref:Microsoft.VisualStudio.Package.TokenTriggers> un desencadenador cuando encuentra un separador de parámetros (a menudo una coma). Esto hace que se actualice una información sobre parámetros y se muestre el siguiente parámetro en negrita. El analizador debe establecer <xref:Microsoft.VisualStudio.Package.TokenTriggers> el valor del desencadenador cuando busque el carácter final de la lista de parámetros (a menudo un paréntesis cercano).

 El <xref:Microsoft.VisualStudio.Package.TokenTriggers> valor del desencadenador inicia <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> una llamada al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método, que a su <xref:Microsoft.VisualStudio.Package.ParseReason>vez llama al analizador de métodos con un motivo de análisis de . Si el analizador determina que el identificador antes del carácter de inicio de la lista de <xref:Microsoft.VisualStudio.Package.AuthoringScope> parámetros es un nombre de método reconocido, devuelve una lista de firmas de método coincidentes en el objeto. Si se encontró alguna firma de método, la información de parámetros se muestra con la primera firma de la lista. Esta información sobre herramientas se actualiza a medida que se escribe más de la firma. Cuando se escribe el carácter final de la lista de parámetros, la información de parámetros se elimina de la vista.

> [!NOTE]
> Para asegurarse de que la información de parámetros información <xref:Microsoft.VisualStudio.Package.Methods> sobre herramientas tiene el formato correcto, debe invalidar las propiedades de la clase para proporcionar los caracteres adecuados. La <xref:Microsoft.VisualStudio.Package.Methods> clase base asume una firma de método de estilo C. Consulte <xref:Microsoft.VisualStudio.Package.Methods> la clase para obtener más información sobre cómo se puede hacer esto.

## <a name="enabling-support-for-the-parameter-info"></a>Habilitación de la compatibilidad con la información de parámetros
 Para admitir la información sobre parámetros, debe establecer el `ShowCompletion` parámetro con nombre de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> en `true`. El servicio de lenguaje lee el valor <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> de esta entrada del Registro de la propiedad.

 Además, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> la propiedad `true` debe establecerse para que se muestre la información de parámetros.

### <a name="example"></a>Ejemplo
 Este es un ejemplo simplificado de detección de los caracteres de la lista de parámetros y la configuración de los desencadenadores adecuados. Este ejemplo es solo para fines ilustrativos. Se supone que el analizador `GetNextToken` contiene un método que identifica y devuelve tokens de una línea de texto. El código de ejemplo simplemente establece los desencadenadores cada vez que ve el tipo correcto de carácter.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Soporte de la información de parámetros en el analizador
 La <xref:Microsoft.VisualStudio.Package.Source> clase hace algunas suposiciones <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> sobre el contenido de las clases y cuando se muestra y actualiza la información de parámetros.

- El analizador se <xref:Microsoft.VisualStudio.Package.ParseReason> proporciona cuando se escribe el carácter de inicio de la lista de parámetros.

- La ubicación indicada <xref:Microsoft.VisualStudio.Package.ParseRequest> en el objeto es inmediatamente después del carácter de inicio de la lista de parámetros. El analizador debe recopilar las firmas de todas las declaraciones de método disponibles <xref:Microsoft.VisualStudio.Package.AuthoringScope> en esa posición y almacenarlas en una lista en la versión del objeto. Esta lista incluye el nombre del método, el tipo de método (o el tipo de valor devuelto) y una lista de parámetros posibles. Más adelante, esta lista se busca la firma o las firmas del método que se mostrarán en la información de parámetros.

  A continuación, el analizador debe analizar <xref:Microsoft.VisualStudio.Package.ParseRequest> la línea especificada por el objeto para recopilar el nombre del método que se está introduciendo, así como la distancia a lo largo del usuario en los parámetros de escritura. Esto se logra pasando el nombre <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> del método <xref:Microsoft.VisualStudio.Package.AuthoringSink> al método <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> en el objeto y, a continuación, <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> llamando al método cuando se analiza el <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> carácter de inicio de la lista de parámetros, llamando al método cuando se analiza el carácter siguiente de la lista de parámetros y, finalmente, llamando al método cuando se analiza el carácter final de la lista de parámetros. La <xref:Microsoft.VisualStudio.Package.Source> clase utiliza los resultados de estas llamadas al método para actualizar la información de parámetros de forma adecuada.

### <a name="example"></a>Ejemplo
 Aquí hay una línea de texto que el usuario puede introducir. Los números debajo de la línea indican qué paso toma el analizador en esa posición en la línea (suponiendo que el análisis se mueve de izquierda a derecha). La suposición aquí es que todo antes de la línea ya se ha analizado para las firmas de método, incluida la firma del método "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Los pasos que toma el analizador se describen a continuación:

1. El analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> llama con el texto "testfunc".

2. El analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>llama .

3. El analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>llama .

4. El analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>llama .
