---
title: "Informaci&#243;n de par&#225;metros en un Service2 de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense, información sobre herramientas de información de parámetros"
  - "Servicios de lenguaje [managed package framework], información de parámetros de IntelliSense"
  - "Información de parámetros (IntelliSense) auxiliares en servicios de lenguaje [managed package framework]"
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Informaci&#243;n de par&#225;metros en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Información de parámetros de IntelliSense es el carácter \(normalmente un paréntesis de apertura\) de la lista de parámetros de método de inicio de una información sobre herramientas que muestra la firma de un método cuando el usuario escribe la lista de parámetros. Como se indica cada parámetro y se escribe el separador de parámetro \(normalmente una coma\), la información sobre herramientas se actualiza para mostrar el siguiente parámetro en negrita.  
  
 Las clases de framework \(MPF\) de paquete administrados proporcionan compatibilidad para administrar la información de parámetros, información sobre herramientas. El analizador debe detectar parámetro parámetro de inicio, a continuación, y los caracteres de fin de parámetros y deben proporcionar una lista de las firmas de método y sus parámetros asociados.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Extender el Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## Implementación  
 El analizador debe establecer el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> se establece cuando encuentra un carácter de inicio de lista de parámetro \(a menudo un paréntesis de apertura\). Se debe establecer un <xref:Microsoft.VisualStudio.Package.TokenTriggers> desencadenar cuando encuentra un separador de parámetro \(a menudo una coma\). Esto hace que una información sobre herramientas de información de parámetros actualizar y mostrar el siguiente parámetro en negrita. El analizador debe establecer el valor desencadenador <xref:Microsoft.VisualStudio.Package.TokenTriggers> cuando si busca el carácter de fin de lista de parámetro \(a menudo un paréntesis de cierre\).  
  
 El <xref:Microsoft.VisualStudio.Package.TokenTriggers> valor desencadenador inicia una llamada a la <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> método, que a su vez llama el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analizador de método con un motivo de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. Si el analizador determina que el identificador antes de la lista de parámetros de carácter de inicio es un nombre de método reconocido, devuelve una lista de hacer coincidir las firmas de método en el <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto. Si se han encontrado las firmas de método, se muestra la información de parámetros, información sobre herramientas con la primera firma en la lista. Esta información sobre herramientas, a continuación, se actualiza como ha escrito más de la firma. Cuando se escribe el carácter de fin de la lista de parámetro, se quita la información de parámetros, información sobre herramientas de la vista.  
  
> [!NOTE]
>  Para garantizar que la información de parámetros, información sobre herramientas es un formato correcto, debe reemplazar las propiedades en la <xref:Microsoft.VisualStudio.Package.Methods> clase para proporcionar los caracteres apropiados. La base de <xref:Microsoft.VisualStudio.Package.Methods> asume la clase de C\#: firma de método de estilo. Consulte la <xref:Microsoft.VisualStudio.Package.Methods> clase para obtener más información sobre cómo puede hacerse.  
  
## Habilitar la compatibilidad para la información de parámetros  
 Para admitir el parámetro información sobre herramientas, debe establecer el `ShowCompletion` con el nombre de parámetro de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> a `true`. El servicio de lenguaje lee el valor de esta entrada del registro desde el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propiedad.  
  
 Además, el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> propiedad debe establecerse en `true` la información de parámetros de información sobre herramientas que se mostrará.  
  
### Ejemplo  
 Este es un ejemplo simplificado de detectar los caracteres de la lista de parámetros y establecer los desencadenadores adecuados. En este ejemplo es sólo con fines ilustrativos. Se supone que el escáner contiene un método `GetNextToken` que identifica y devuelve símbolos \(tokens\) de una línea de texto. El código de ejemplo simplemente establece los desencadenadores cada vez que detecta el tipo de carácter.  
  
```c#  
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
  
## Compatibilidad con la información de parámetros, información sobre herramientas en el analizador  
 La <xref:Microsoft.VisualStudio.Package.Source> clase hace algunas suposiciones sobre el contenido de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> y <xref:Microsoft.VisualStudio.Package.AuthoringSink> clases cuando se muestran y se actualiza la información de parámetros, información sobre herramientas.  
  
-   Se proporciona el analizador <xref:Microsoft.VisualStudio.Package.ParseReason> cuando se escribe el carácter de inicio de la lista de parámetros.  
  
-   La ubicación en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto es inmediatamente después de la lista de parámetros de carácter de inicio. El analizador debe recopilar las firmas de todas las declaraciones de método disponibles en el que colocan y almacenan en una lista de la versión de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto. Esta lista incluye el nombre del método, tipo de método \(o tipo de valor devuelto\) y una lista de parámetros posibles. Esta lista más adelante se busca la firma del método o firmas para mostrar la información de parámetros, información sobre herramientas.  
  
 El analizador, a continuación, debe analizar la línea especificada por el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto que se va a recopilar el nombre del método que se especifica, así como la distancia a lo largo del usuario es escribir parámetros. Esto se consigue pasando el nombre del método para el <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> método en el <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto y, a continuación, llamar a la <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> al carácter de inicio de la lista de parámetros de método se analiza, llamar a la <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> cuando se analiza el carácter siguiente de lista de parámetros de método y finalmente llamando a la <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> cuando se analiza el carácter de fin de la lista de parámetro de método. Los resultados de estas llamadas al método se utilizan por el <xref:Microsoft.VisualStudio.Package.Source> clase para actualizar la información de parámetros, información sobre herramientas adecuadamente.  
  
### Ejemplo  
 Aquí es una línea de texto que se puede escribir el usuario. Los números de debajo de la línea indican qué paso se realiza por el analizador en esa posición en la línea \(suponiendo que el análisis se mueve de izquierda a derecha\). La suposición aquí es que todo el contenido antes de la línea ya se ha analizado para firmas de método, incluida la firma del método "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Los pasos que toma el analizador se describen a continuación:  
  
1.  Las llamadas de analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> con el texto "testfunc".  
  
2.  Las llamadas de analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Las llamadas de analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Las llamadas de analizador <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.