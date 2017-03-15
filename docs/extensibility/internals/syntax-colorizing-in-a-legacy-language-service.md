---
title: "Coloreado de sintaxis en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje [managed package framework], resaltado de sintaxis"
  - "colores, auxiliares en servicios de lenguaje [managed package framework]"
  - "sintaxis de resaltado, auxiliares en servicios de lenguaje [managed package framework]"
  - "Servicios de lenguaje [managed package framework], colores"
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Coloreado de sintaxis en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Colores de sintaxis es una característica que hace que los diferentes elementos del lenguaje de programación que se mostrará en un archivo de origen en diferentes colores y estilos. Para admitir esta característica, deberá suministrar un analizador o escáner que puede identificar los tipos de elementos léxicos o tokens en el archivo. Muchos lenguajes distinguen delimitadores \(como paréntesis o llaves\), palabras clave y los comentarios por ellos colorear de maneras diferentes.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Extender el Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## Implementación  
 Para admitir la coloración, el marco de trabajo de paquete administrado \(MPF\) incluye la <xref:Microsoft.VisualStudio.Package.Colorizer> clase que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaz. Esta clase interactúa con un <xref:Microsoft.VisualStudio.Package.IScanner> para determinar el símbolo \(token\) y colores. Para obtener más información sobre escáneres, consulte [Escáneres y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer> clase, a continuación, marca cada carácter del token con la información de color y devuelve esa información al editor de mostrar el archivo de origen.  
  
 La información de color devuelta al editor es un índice en una lista de elementos coloreables. Cada elemento coloreable especifica un valor de color y un conjunto de atributos de fuente, como negrita o tachado. El editor proporciona un conjunto de elementos coloreable predeterminados que puede utilizar el servicio de lenguaje. Todo lo que necesita hacer es especificar el índice de color adecuado para cada tipo de token. Sin embargo, puede proporcionar un conjunto de elementos coloreables personalizados y los índices que se proporciona para los tokens y hacen referencia a su propia lista de elementos coloreables en lugar de la lista predeterminada. También debe establecer el `RequestStockColors` entrada del registro en 0 \(o no especifique el `RequestStockColors` entrada en absoluto\) para admitir los colores personalizados. Puede establecer esta entrada del registro con un parámetro con nombre para el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo definido por el usuario. Para obtener más información acerca de registrar un servicio de lenguaje y establecer sus opciones, consulte [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## Elementos coloreables personalizados  
 Para proporcionar sus propios elementos coloreables personalizados, debe reemplazar el <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> y <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. El primer método devuelve el número de elementos coloreables personalizados que admita el servicio de lenguaje y la segunda obtiene el elemento coloreable personalizado por índice. Crear la lista predeterminada de elementos coloreables personalizados. En el constructor de su servicio de lenguaje, todo lo que necesita hacer es proporcionar cada elemento coloreable con un nombre. Visual Studio controla automáticamente el caso donde el usuario selecciona un conjunto diferente de elementos coloreables. Este nombre es lo que aparece en el **fuentes y colores** página de propiedades en el **opciones** cuadro de diálogo \(disponible en Visual Studio **herramientas** menú\) y este nombre determina el color que un usuario ha invalidado. Las opciones del usuario se almacenan en una caché en el registro y acceso por el nombre del color. El **fuentes y colores** página de propiedades muestra todos los nombres de colores en orden alfabético, por lo que puede agrupar sus colores personalizados por delante de cada nombre de color con el nombre de idioma; por ejemplo, "**TestLanguage \- comentario**"y"**TestLanguage \- Keyword**". O puede agrupar los elementos por tipo, coloreables "**comentario \(TestLanguage\)**"y"**\(palabra clave\) \(TestLanguage\)**". Se prefiere la agrupación por nombre de idioma.  
  
> [!CAUTION]
>  Se recomienda que incluya el nombre del idioma en el nombre del elemento coloreable para evitar conflictos con los nombres de elemento coloreable existentes.  
  
> [!NOTE]
>  Si cambia el nombre de uno de los colores durante el desarrollo, debe restablecer la memoria caché que Visual Studio crea la primera vez que se tuvo acceso a sus colores. Puede hacerlo ejecutando el **Restablecer el subárbol Experimental** comando en el menú del programa de Visual Studio SDK.  
  
 Tenga en cuenta que el primer elemento en la lista de elementos coloreables nunca se hace referencia. Visual Studio proporciona siempre los colores predeterminados de texto y los atributos de ese elemento. La manera más fácil de tratar esto es proporcionar un elemento coloreable de marcador de posición como el primer elemento.  
  
### Color de alta densidad coloreable elementos  
 Elementos coloreables también admiten valores de color de 24 bits o alto a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz. La MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> clase admite la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz y los colores de 24 bits que se especifican en el constructor junto con los colores normales. Consulte la <xref:Microsoft.VisualStudio.Package.ColorableItem> clase para obtener más detalles. En el ejemplo siguiente se muestra cómo establecer los colores de 24 bits de palabras clave y comentarios. Los colores de 24 bits que se utilizan al color de 24 bits es compatible con el escritorio del usuario; de lo contrario, se utilizan los colores de texto normal.  
  
 Recuerde que éstos son los colores predeterminados para el lenguaje; el usuario puede cambiar estos colores según sus preferencias.  
  
### Ejemplo  
 Este ejemplo muestra una manera de declarar y rellenar una matriz de elementos coloreables personalizados mediante la <xref:Microsoft.VisualStudio.Package.ColorableItem> clase. Este ejemplo establece los colores de la palabra clave y el comentario utilizando colores de 24 bits.  
  
```c#  
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
  
## La clase aplicador de color y el analizador  
 La base de <xref:Microsoft.VisualStudio.Package.LanguageService> clase tiene un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> método que instantiantes la <xref:Microsoft.VisualStudio.Package.Colorizer> clase. El analizador que se devuelve desde el <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método se pasa a la <xref:Microsoft.VisualStudio.Package.Colorizer> constructor de clase.  
  
 Debe implementar la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método en su propia versión de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase utiliza el escáner para obtener toda la información de color de token.  
  
 El analizador debe rellenar un <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura para cada token busca. Esta estructura contiene información como la duración del token ocupa, el índice de color utilizar, qué tipo es el tokens y el tokens de desencadenadores \(consulte <xref:Microsoft.VisualStudio.Package.TokenTriggers>\). Sólo el índice de intervalo y el color se necesitan para coloración por la <xref:Microsoft.VisualStudio.Package.Colorizer> clase.  
  
 El índice de color se almacena en el <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura suele ser un valor de la <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración, que proporciona una serie de índices con nombre correspondiente a los diversos elementos del lenguaje como palabras clave y operadores. Si los elementos coloreables personalizados en la lista coincide con los elementos se presentan en el <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración, entonces, puede simplemente utilice la enumeración como el color de cada token. Sin embargo, si tiene elementos coloreables adicionales o no desea utilizar los valores existentes en ese orden, puede organizar la lista de elementos coloreable personalizado para satisfacer sus necesidades y devolver el índice adecuado en esa lista. Asegúrese de convertir el índice de un <xref:Microsoft.VisualStudio.Package.TokenColor> al almacenarlos en el <xref:Microsoft.VisualStudio.Package.TokenInfo> estructura [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] ve sólo el índice.  
  
### Ejemplo  
 En el ejemplo siguiente se muestra cómo el analizador puede identificar los tres tipos de tokens: identificadores \(algo que no es un número o signos de puntuación\), signos de puntuación y números. Este ejemplo es para fines ilustrativos únicamente y no representa una implementación completa de analizador y el analizador. Se supone que existe una `Lexer` clase con un `GetNextToken()` método que devuelve una cadena.  
  
```c#  
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
  
## Vea también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Escáneres y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md)