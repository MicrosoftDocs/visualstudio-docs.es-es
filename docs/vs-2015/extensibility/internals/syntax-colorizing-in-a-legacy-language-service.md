---
title: Coloreado de sintaxis en un servicio de lenguaje heredado | Documentos de Microsoft
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
ms.openlocfilehash: 585208150047b32adfdac916146268751a2a1287
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995028"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Coloreado de sintaxis en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Coloración de sintaxis es una característica que hace que los diferentes elementos de un lenguaje de programación que se mostrará en un archivo de código fuente de distintos colores y estilos. Para admitir esta característica, deberá suministrar un analizador o un escáner que puede identificar los tipos de elementos léxicos o símbolos (tokens) en el archivo. Muchos lenguajes para distinguir las palabras clave, delimitadores (como paréntesis o llaves) y los comentarios, colorear ellas de maneras diferentes.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información, consulte [ampliación del Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="implementation"></a>Implementación  
 Para admitir la coloración, managed package framework (MPF) incluye la <xref:Microsoft.VisualStudio.Package.Colorizer> clase que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz. Esta clase interactúa con un <xref:Microsoft.VisualStudio.Package.IScanner> para determinar el símbolo (token) y los colores. Para obtener más información sobre los analizadores, consulte [analizador del servicio de lenguaje heredado y el analizador](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer> clase, a continuación, marca cada carácter del token con la información de color y devuelve esa información en el editor muestra el archivo de origen.  
  
 La información de color que se devuelve al editor es un índice en una lista de elementos coloreables. Cada elemento coloreable especifica un valor de color y un conjunto de atributos de fuente, como negrita o tachado. El editor proporciona un conjunto de elementos coloreables predeterminados que puede usar el servicio de lenguaje. Todo lo que necesita hacer es especificar el índice de color apropiado para cada tipo de token. Sin embargo, puede proporcionar un conjunto de elementos coloreables personalizados y los índices que se proporciona para los tokens y hacen referencia a su propia lista de elementos coloreables en lugar de la lista predeterminada. También debe establecer el `RequestStockColors` entrada del registro en 0 (o no especifique el `RequestStockColors` entrada en absoluto) para admitir los colores personalizados. Puede establecer esta entrada del registro con un parámetro con nombre para el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo definido por el usuario. Para obtener más información acerca de registrar un servicio de lenguaje y establecer sus opciones, consulte [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Elementos coloreables personalizados  
 Para proporcionar sus propios elementos coloreables personalizados, debe invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> y <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> método en el <xref:Microsoft.VisualStudio.Package.LanguageService> clase. El primer método devuelve el número de elementos coloreables personalizados que admite el servicio de lenguaje y la segunda obtiene el elemento coloreable personalizado por índice. Crear la lista predeterminada de elementos coloreables personalizados. En el constructor de su servicio de lenguaje, todo lo que necesita hacer es proporcionar cada elemento coloreable con un nombre. Visual Studio controla automáticamente el caso donde el usuario selecciona un conjunto diferente de elementos coloreables. Este nombre es lo que aparece en el **fuentes y colores** página de propiedades en el **opciones** cuadro de diálogo (disponible en Visual Studio **herramientas** menú) y este nombre determina a qué color de que un usuario ha invalidado. Las opciones del usuario se almacena en una caché en el registro y accesible para el nombre del color. El **fuentes y colores** página de propiedades enumera todos los nombres de colores en orden alfabético, por lo que puede agrupar sus colores personalizados utilizando delante de cada nombre de color con el nombre del lenguaje; por ejemplo, "**TestLanguage comentarios**"y"**TestLanguage - Keyword**". O puede agrupar los elementos coloreables por tipo, "**comentario (TestLanguage)**"y"**palabra clave (TestLanguage)**". Se prefiere la agrupación por nombre de idioma.  
  
> [!CAUTION]
>  Se recomienda encarecidamente que incluyen el nombre del idioma en el nombre del elemento coloreable para evitar conflictos con otros nombres de elemento coloreable.  
  
> [!NOTE]
>  Si cambia el nombre de uno de sus colores durante el desarrollo, debe restablecer la memoria caché que Visual Studio crea la primera vez que se han accedido a los colores. Puede hacerlo ejecutando el **restablecer el subárbol Experimental** comando en el menú del programa de Visual Studio SDK.  
  
 Tenga en cuenta que el primer elemento en la lista de elementos coloreables nunca se hace referencia. Visual Studio proporciona siempre los colores de texto predeterminado y atributos para ese elemento. La manera más fácil de tratar con esto es proporcionar un elemento coloreable de marcador de posición como el primer elemento.  
  
### <a name="high-color-colorable-items"></a>Elementos coloreables del color de alta densidad  
 Elementos coloreables también pueden admitir valores de color de 24 bits o de alta a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> clase admite la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz y los colores de 24 bits se especifican en el constructor junto con los colores normales. Vea la clase <xref:Microsoft.VisualStudio.Package.ColorableItem> para obtener información más detallada. El ejemplo siguiente muestra cómo establecer los colores de 24 bits por palabras clave y comentarios. Se usan los colores de 24 bits al color de 24 bits es compatible con el escritorio del usuario; en caso contrario, se usan los colores de texto normal.  
  
 Recuerde, que éstas son los colores predeterminados para el lenguaje; el usuario puede cambiar estos colores según sus preferencias.  
  
### <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo declarar y rellenar una matriz de elementos coloreables personalizados mediante el <xref:Microsoft.VisualStudio.Package.ColorableItem> clase. Este ejemplo establece los colores de la palabra clave y el comentario utilizando los colores de 24 bits.  
  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>La clase Coloreador y el analizador  
 La base de <xref:Microsoft.VisualStudio.Package.LanguageService> clase tiene un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> método ese instantiantes la <xref:Microsoft.VisualStudio.Package.Colorizer> clase. El analizador que se devuelve desde el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método se pasa a la <xref:Microsoft.VisualStudio.Package.Colorizer> constructor de clase.  
  
 Debe implementar la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en su propia versión de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase utiliza el escáner para obtener toda la información de token de color.  
  
 El analizador debe rellenar un <xref:Microsoft.VisualStudio.Package.TokenInfo> de estructura para todos los tokens busca. Esta estructura contiene información como el intervalo, el token ocupa, el índice de color que se utilizará, qué tipo es el tokens y tokens de desencadenadores (consulte <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Solo el índice de intervalo y el color son necesarios para la coloración por la <xref:Microsoft.VisualStudio.Package.Colorizer> clase.  
  
 El índice de color se almacena en el <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura suele ser un valor de la <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración, que proporciona un número de índices con nombre correspondiente a los diversos elementos del lenguaje como palabras clave y operadores. Si los elementos coloreables personalizados en la lista coincide con los elementos se presentan en el <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración, puede simplemente usar la enumeración como el color para cada token. Sin embargo, si tiene elementos coloreables adicionales o no desea utilizar los valores existentes en ese orden, puede organizar la lista de elementos coloreables personalizados para satisfacer sus necesidades y devolver el índice adecuado en esa lista. Asegúrese de convertir el índice de un <xref:Microsoft.VisualStudio.Package.TokenColor> cuando se almacenan en el <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura; [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] ve solo el índice.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo el analizador podría identificar tres tipos de token: números, signos de puntuación y los identificadores (todo lo que no es un número o signos de puntuación). En este ejemplo es para fines ilustrativos únicamente y no representa una implementación integral de analizador y el analizador. Se supone que hay un `Lexer` clase con un `GetNextToken()` método que devuelve una cadena.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)
