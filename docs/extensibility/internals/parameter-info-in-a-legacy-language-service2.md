---
title: "Información de parámetros en un Service2 de lenguaje heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d806c48cd96c93774b77363f1d427968613e60b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Información de parámetros en un servicio de lenguaje heredado
Información de parámetros de IntelliSense es el carácter (normalmente un paréntesis de apertura) para la lista de parámetros de método de inicio de una información sobre herramientas que muestra la firma de un método cuando el usuario escribe la lista de parámetros. Tal y como se escribe cada parámetro y se ha escrito el separador de parámetros (normalmente una coma), la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita.  
  
 Las clases de managed package framework (MPF) proporcionan compatibilidad para administrar la información de parámetros, información sobre herramientas. El analizador debe detectar parámetro parámetro de inicio, a continuación, y los caracteres de fin de parámetro y deben proporcionar una lista de las firmas de método y sus parámetros asociados.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información, consulte [extender el Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="implementation"></a>Implementación  
 El analizador debe establecer el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> se establece cuando encuentra un carácter de inicio de lista de parámetro (a menudo un paréntesis de apertura). Se debe establecer un <xref:Microsoft.VisualStudio.Package.TokenTriggers> desencadenar cuando encuentra un separador de parámetro (a menudo una coma). Esto hace que una información sobre herramientas de información de parámetros actualizar y mostrar el siguiente parámetro en negrita. El analizador debe establecer el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> cuando si busca el carácter de final de lista de parámetro (a menudo un paréntesis de cierre).  
  
 El <xref:Microsoft.VisualStudio.Package.TokenTriggers> valor desencadenador inicia una llamada a la <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> método, que a su vez llama a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizador de método con un motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. Si el analizador determina que el identificador antes de carácter de inicio de la lista de parámetros es un nombre de método reconocido, devuelve una lista de hacer coincidir las firmas de método en el <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto. Si se han encontrado las firmas de método, se muestra la información de parámetros, información sobre herramientas con la primera firma en la lista. Esta información sobre herramientas, a continuación, se actualiza mientras se escribe más de la firma. Cuando se escribe el carácter de final de lista de parámetros, se quita la información de parámetros, información sobre herramientas de vista.  
  
> [!NOTE]
>  Para asegurarse de que la información de parámetros, información sobre herramientas tiene el formato adecuado, debe invalidar las propiedades en la <xref:Microsoft.VisualStudio.Package.Methods> clase para proporcionar los caracteres apropiados. La base de <xref:Microsoft.VisualStudio.Package.Methods> se da por supuesto la clase C#: firma de método de estilo. Consulte la <xref:Microsoft.VisualStudio.Package.Methods> clase para obtener más información sobre cómo hacerlo.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Habilitar la compatibilidad para la información de parámetros  
 Para admitir la información de parámetros información sobre herramientas, debe establecer el `ShowCompletion` con el nombre de parámetro de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> a `true`. El servicio de lenguaje lee el valor de esta entrada del registro de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad.  
  
 Además, el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> propiedad debe establecerse en `true` para la información de parámetros de información sobre herramientas que se mostrará.  
  
### <a name="example"></a>Ejemplo  
 Este es un ejemplo simplificado de detectar los caracteres de la lista de parámetros y establecer los desencadenadores adecuados. En este ejemplo es solo con fines ilustrativos. Se supone que el escáner contiene un método `GetNextToken` que identifica y devuelve símbolos (tokens) de una línea de texto. El código de ejemplo establece simplemente los desencadenadores cada vez que detecta el tipo correcto de caracteres.  
  
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
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Compatibilidad con la información de parámetros, información sobre herramientas en el analizador  
 El <xref:Microsoft.VisualStudio.Package.Source> clase hace algunas suposiciones sobre el contenido de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> y <xref:Microsoft.VisualStudio.Package.AuthoringSink> clases cuando la información de parámetros, información sobre herramientas se muestran y se han actualizado.  
  
-   Se proporciona el analizador <xref:Microsoft.VisualStudio.Package.ParseReason> cuando se escribe el carácter de inicio de la lista de parámetros.  
  
-   La ubicación en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto está inmediatamente después de carácter de inicio de la lista de parámetros. El analizador debe recopilar las firmas de todas las declaraciones de método disponibles en el que colocar y almacenan en una lista en la versión de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto. Esta lista incluye el nombre del método, tipo de método (o tipo de valor devuelto) y una lista de parámetros posibles. Más adelante se busca esta lista para que la firma del método o firmas para mostrar en la información de parámetros, información sobre herramientas.  
  
 El analizador, a continuación, debe analizar la línea especificada por el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto que se va a recopilar el nombre del método que se especifiquen, así como de hasta qué punto a lo largo del usuario está escritura de los parámetros. Esto se consigue pasando el nombre del método que se la <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> método en el <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto y, a continuación, llamar a la <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> se analiza al carácter de inicio de la lista de parámetros de método, una llamada a la <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> método cuando la lista de parámetros siguiente carácter se analiza y por último, que realiza la llamada la <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> método cuando se analiza el carácter de final de lista de parámetros. Los resultados de estas llamadas al método se usan por el <xref:Microsoft.VisualStudio.Package.Source> clase para actualizar correctamente la información de parámetros, información sobre herramientas.  
  
### <a name="example"></a>Ejemplo  
 Esta es una línea de texto que se puede escribir el usuario. Los números situados debajo de la línea indican qué pasos debe realizarse en el analizador en esa posición de la línea (suponiendo que el análisis de movimientos de izquierda a derecha). La suposición aquí es que todo el contenido antes de la línea ya se ha analizado para las firmas de método, que incluye la firma de método "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Los pasos que efectúa el analizador se describen a continuación:  
  
1.  Las llamadas de analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> con el texto "testfunc".  
  
2.  Las llamadas de analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Las llamadas de analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Las llamadas de analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.