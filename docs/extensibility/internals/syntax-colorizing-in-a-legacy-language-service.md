---
title: Coloreado de sintaxis en un servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d82a85958fd979a3d9d44375656b08356ef09d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Coloreado de sintaxis en un servicio de lenguaje heredado
Colores de sintaxis es una característica que hace que los diferentes elementos de un lenguaje de programación que se mostrará en un archivo de código fuente de diferentes colores y estilos. Para admitir esta característica, deberá suministrar un analizador o un escáner que puede identificar los tipos de elementos léxicos o tokens en el archivo. Muchos lenguajes distinguen palabras clave, delimitadores (por ejemplo, los paréntesis o llaves) y comentarios por ellos coloreado de maneras diferentes.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información, consulte [extender el Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="implementation"></a>Implementación  
 Para admitir la coloración, managed package framework (MPF) incluye la <xref:Microsoft.VisualStudio.Package.Colorizer> de la clase, que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz. Esta clase interactúa con un <xref:Microsoft.VisualStudio.Package.IScanner> para determinar el símbolo (token) y colores. Para obtener más información sobre escáneres, consulte [analizador del servicio de lenguaje heredado y el analizador](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer> clase, a continuación, marca cada carácter del token con la información de color y devuelve esa información en el editor muestra el archivo de origen.  
  
 La información de color devuelta al editor es un índice en una lista de elementos coloreables. Cada elemento coloreable especifica un valor de color y un conjunto de atributos de fuente, como negrita o tachado. El editor proporciona un conjunto de elementos coloreable predeterminados que puede usar el servicio de lenguaje. Todo lo que necesita hacer es especificar el índice de color adecuado para cada tipo de token. Sin embargo, puede proporcionar un conjunto de elementos coloreables personalizados y los índices que se proporciona para los tokens y hacen referencia a su propia lista de elementos coloreables en lugar de la lista predeterminada. También debe establecer el `RequestStockColors` entrada del registro en 0 (o no especifique el `RequestStockColors` entrada en absoluto) para admitir los colores personalizados. Puede establecer esta entrada del registro con un parámetro con nombre para el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo definido por el usuario. Para obtener más información acerca de registrar un servicio de lenguaje y establecer sus opciones, consulte [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Elementos coloreables personalizados  
 Para proporcionar sus propios elementos coloreables personalizados, debe invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> y <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. El primer método devuelve el número de elementos coloreables personalizados que admita el servicio de lenguaje y la segunda obtiene el elemento coloreable personalizado por índice. Crear la lista predeterminada de elementos coloreables personalizados. En el constructor de su servicio de lenguaje, todo lo que necesita hacer es proporcionar cada elemento coloreable con un nombre. Visual Studio controla automáticamente el caso donde el usuario selecciona un conjunto de elementos coloreables diferente. Este nombre es lo que aparece en el **fuentes y colores** página de propiedades en el **opciones** cuadro de diálogo (disponible en Visual Studio **herramientas** menú) y este nombre determina a qué color de que un usuario ha invalidado. Las opciones del usuario se almacenan en una memoria caché en el registro y se tiene acceso con el nombre del color. El **fuentes y colores** página de propiedades enumera todos los nombres de color en orden alfabético, por lo que puede agrupar los colores personalizados utilizando delante de cada nombre de color con el nombre del lenguaje; por ejemplo, "**TestLanguage comentarios**"y"**TestLanguage - Keyword**". O puede agrupar los elementos por tipo, coloreables "**comentario (TestLanguage)**"y"**palabra clave (TestLanguage)**". Agrupar por nombre de idioma es preferible.  
  
> [!CAUTION]
>  Se recomienda que incluya el nombre de idioma en el nombre del elemento coloreable para evitar conflictos con los nombres de elemento coloreable existentes.  
  
> [!NOTE]
>  Si cambia el nombre de uno de los colores durante el desarrollo, debe restablecer la memoria caché que Visual Studio crea la primera vez que se tiene acceso a sus colores. Puede hacerlo ejecutando el **restablecer el subárbol Experimental** comando en el menú de programa del SDK de Visual Studio.  
  
 Tenga en cuenta que el primer elemento en la lista de elementos coloreables nunca se hace referencia. Visual Studio proporciona siempre los colores predeterminados de texto y los atributos de ese elemento. La manera más fácil de tratar con esto es proporcionar un elemento coloreable de marcador de posición como el primer elemento.  
  
### <a name="high-color-colorable-items"></a>Color de alta densidad coloreable elementos  
 Elementos coloreables también pueden admitir valores de color de 24 bits o alto a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> clase admite la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz y los colores de 24 bits que se especifican en el constructor junto con los colores normales. Vea la clase <xref:Microsoft.VisualStudio.Package.ColorableItem> para obtener información más detallada. En el ejemplo siguiente se muestra cómo establecer los colores de 24 bits de palabras clave y comentarios. Los colores de 24 bits se utilizan al color de 24 bits es compatible con el escritorio del usuario; en caso contrario, se utilizan los colores de texto normal.  
  
 Recuerde que éstos son los colores predeterminados para el lenguaje; el usuario puede cambiar estos colores a todo lo deseen.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra una manera de declarar y rellenar una matriz de elementos coloreables personalizados mediante la <xref:Microsoft.VisualStudio.Package.ColorableItem> clase. Este ejemplo establece los colores de palabra clave y el comentario utilizando los colores de 24 bits.  
  
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
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>La clase aplicador de color y el analizador  
 La base de <xref:Microsoft.VisualStudio.Package.LanguageService> clase tiene un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> método ese instantiantes la <xref:Microsoft.VisualStudio.Package.Colorizer> clase. El escáner que se devuelve desde el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método se pasa a la <xref:Microsoft.VisualStudio.Package.Colorizer> constructor de clase.  
  
 Debe implementar la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en su propia versión de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase utiliza el escáner para obtener toda la información de símbolo (token) de color.  
  
 El escáner es necesario rellenar un <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura para cada token busca. Esta estructura contiene información como el intervalo el token ocupa, el índice de color que se utilizará, qué tipo es los desencadenadores de símbolo (token) y símbolo (token) (consulte <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Solo el índice de intervalo y el color son necesarios para coloración por la <xref:Microsoft.VisualStudio.Package.Colorizer> clase.  
  
 Almacena el índice de color en la <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura suele ser un valor comprendido entre el <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración, que proporciona una serie de índices con nombre que se corresponden a diversos elementos del lenguaje, como palabras clave y operadores. Si los elementos coloreables personalizados en la lista coincide con los elementos se presentan en el <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración; a continuación, puede utilizar la enumeración como el color para cada token. Sin embargo, si tiene elementos coloreables adicionales o no desea usar los valores existentes en ese orden, puede organizar la lista de elementos coloreable personalizado para satisfacer sus necesidades y devuelve el índice adecuado en esa lista. Asegúrese de convertir el índice de un <xref:Microsoft.VisualStudio.Package.TokenColor> cuando se almacenan en la <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] ve únicamente en el índice.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo el analizador podría identificar tres tipos de tokens: identificadores (todo lo que no es un número o signos de puntuación), números y signos de puntuación. Este ejemplo es para fines ilustrativos únicamente y no representa una implementación completa de analizador y el analizador. Se supone que hay un `Lexer` clase con un `GetNextToken()` método que devuelve una cadena.  
  
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
 [Escáneres y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)