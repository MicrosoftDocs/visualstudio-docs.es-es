---
title: Coloración de la sintaxis en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64e57ebc80320ccc133261781eb8ee6611c8e2a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843039"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Coloreado de sintaxis en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La coloración de la sintaxis es una característica que hace que los distintos elementos de un lenguaje de programación se muestren en un archivo de código fuente con distintos colores y estilos. Para admitir esta característica, debe proporcionar un analizador o un escáner que pueda identificar los tipos de elementos o tokens léxicos en el archivo. Muchos idiomas distinguen las palabras clave, los delimitadores (como paréntesis o llaves) y los comentarios al colorearlos de maneras diferentes.  
  
 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información, vea [extender el editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.  
  
## <a name="implementation"></a>Implementación  
 Para admitir la coloración, el marco de trabajo de paquetes administrados (MPF) incluye la <xref:Microsoft.VisualStudio.Package.Colorizer> clase, que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz. Esta clase interactúa con <xref:Microsoft.VisualStudio.Package.IScanner> para determinar el token y los colores. Para obtener más información acerca de los escáneres, consulte [analizador y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer>A continuación, la clase marca cada carácter del token con la información de color y devuelve esa información al editor que muestra el archivo de código fuente.  
  
 La información de color devuelta al editor es un índice en una lista de elementos coloreables. Cada elemento coloreable especifica un valor de color y un conjunto de atributos de fuente, como negrita o tachado. El editor proporciona un conjunto de elementos coloreables predeterminados que puede usar el servicio de lenguaje. Lo único que debe hacer es especificar el índice de color adecuado para cada tipo de token. Sin embargo, puede proporcionar un conjunto de elementos coloreables personalizados y los índices que proporcione para los tokens, y hacer referencia a su propia lista de elementos coloreables en lugar de la lista predeterminada. También debe establecer la `RequestStockColors` entrada del registro en 0 (o no especificar la `RequestStockColors` entrada en absoluto) para admitir los colores personalizados. Puede establecer esta entrada del registro con un parámetro con nombre en el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo definido por el usuario. Para obtener más información sobre cómo registrar un servicio de lenguaje y establecer sus opciones, consulte [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Elementos coloreables personalizados  
 Para proporcionar sus propios elementos coloreables personalizados, debe invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> método y en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. El primer método devuelve el número de elementos coloreables personalizados que admite el servicio de lenguaje y el segundo obtiene el elemento coloreable personalizado por índice. Se crea la lista predeterminada de elementos coloreables personalizados. En el constructor del servicio de lenguaje, lo único que debe hacer es proporcionar un nombre a cada elemento coloreable. Visual Studio controla automáticamente el caso en el que el usuario selecciona un conjunto diferente de elementos coloreables. Este nombre es lo que aparece en la página de propiedades **fuentes y colores** del cuadro de diálogo **Opciones** (disponible en el menú **herramientas** de Visual Studio) y este nombre determina qué color ha invalidado un usuario. Las opciones del usuario se almacenan en una caché del registro y se obtiene acceso a ellas mediante el nombre del color. En la página de propiedades **fuentes y colores** se enumeran todos los nombres de colores en orden alfabético, de modo que puede agrupar los colores personalizados antes de cada nombre de color con su nombre de idioma; por ejemplo, "**TestLanguage-comment**" y "**TestLanguage-keyword**". O bien, puede agrupar los elementos coloreables por tipo, "**Comentario (TestLanguage)**" y "**palabra clave (TestLanguage)**". Se prefiere la agrupación por nombre de lenguaje.  
  
> [!CAUTION]
> Se recomienda que incluya el nombre de idioma en el nombre del elemento coloreable para evitar colisiones con los nombres de elementos coloreables existentes.  
  
> [!NOTE]
> Si cambia el nombre de uno de los colores durante el desarrollo, debe restablecer la memoria caché que Visual Studio creó la primera vez que se tuvo acceso a los colores. Puede hacerlo mediante la ejecución del comando **restablecer el subárbol experimental** desde el menú del programa del SDK de Visual Studio.  
  
 Tenga en cuenta que nunca se hace referencia al primer elemento de la lista de elementos coloreables. Visual Studio siempre proporciona los colores de texto y los atributos predeterminados para ese elemento. La manera más sencilla de trabajar con esto es proporcionar un elemento coloreable de marcador de posición como primer elemento.  
  
### <a name="high-color-colorable-items"></a>Elementos coloreables de color alto  
 Los elementos coloreables también pueden admitir valores de color de 24 bits o alto a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz. La <xref:Microsoft.VisualStudio.Package.ColorableItem> clase MPF admite la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz y los colores de 24 bits se especifican en el constructor junto con los colores normales. Vea la clase <xref:Microsoft.VisualStudio.Package.ColorableItem> para obtener información más detallada. En el ejemplo siguiente se muestra cómo establecer los colores de 24 bits para palabras clave y comentarios. Los colores de 24 bits se utilizan cuando se admite el color de 24 bits en el escritorio del usuario. de lo contrario, se usan los colores de texto normales.  
  
 Recuerde que estos son los colores predeterminados para su idioma; el usuario puede cambiar estos colores a cualquier cosa que desee.  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra una manera de declarar y rellenar una matriz de elementos coloreables personalizados mediante la <xref:Microsoft.VisualStudio.Package.ColorableItem> clase. En este ejemplo se establecen los colores de palabras clave y comentarios con colores de 24 bits.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>La clase de coloreador y el escáner  
 La <xref:Microsoft.VisualStudio.Package.LanguageService> clase base tiene un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> método que instantiantes la <xref:Microsoft.VisualStudio.Package.Colorizer> clase. El analizador que se devuelve desde el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método se pasa al <xref:Microsoft.VisualStudio.Package.Colorizer> constructor de clase.  
  
 Debe implementar el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en su propia versión de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase usa el escáner para obtener toda la información de color del token.  
  
 El analizador tiene que rellenar una <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura para cada token que encuentre. Esta estructura contiene información como el intervalo que ocupa el token, el índice de color que se va a usar, el tipo de token y los desencadenadores de token (vea <xref:Microsoft.VisualStudio.Package.TokenTriggers> ). Solo el intervalo y el índice de color son necesarios para la coloración de la <xref:Microsoft.VisualStudio.Package.Colorizer> clase.  
  
 Normalmente, el índice de color almacenado en la <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura es un valor de la <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración, que proporciona varios índices con nombre correspondientes a varios elementos del lenguaje como palabras clave y operadores. Si la lista de elementos coloreables personalizados coincide con los elementos presentados en la <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración, puede usar simplemente la enumeración como color para cada token. Sin embargo, si tiene elementos coloreables adicionales o no desea usar los valores existentes en ese orden, puede organizar la lista de elementos coloreables personalizados para que se adapte a sus necesidades y devolver el índice adecuado en esa lista. Asegúrese de convertir el índice a un <xref:Microsoft.VisualStudio.Package.TokenColor> al almacenarlo en la <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura; [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] solo ve el índice.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo el analizador puede identificar tres tipos de token: números, signos de puntuación e identificadores (cualquier elemento que no sea un número o un signo de puntuación). Este ejemplo se utiliza únicamente con fines ilustrativos y no representa una implementación completa del analizador y del analizador. Se supone que hay una `Lexer` clase con un `GetNextToken()` método que devuelve una cadena.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>Consulte también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Analizador y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)
