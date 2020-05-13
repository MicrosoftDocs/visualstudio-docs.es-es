---
title: Coloreación de sintaxis en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704708"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Coloreado de sintaxis en un servicio de lenguaje heredado
La coloración de sintaxis es una característica que hace que diferentes elementos de un lenguaje de programación se muestren en un archivo de origen en diferentes colores y estilos. Para admitir esta característica, debe proporcionar un analizador o escáner que pueda identificar los tipos de elementos léxicos o tokens en el archivo. Muchos idiomas distinguen palabras clave, delimitadores (como paréntesis o llaves) y comentarios colorizándolos de diferentes maneras.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Ampliación del editor y](../../extensibility/extending-the-editor-and-language-services.md)los servicios de lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="implementation"></a>Implementación
 Para admitir la coloración, el marco <xref:Microsoft.VisualStudio.Package.Colorizer> de paquete administrado <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> (MPF) incluye la clase, que implementa la interfaz. Esta clase interactúa <xref:Microsoft.VisualStudio.Package.IScanner> con un para determinar el token y los colores. Para obtener más información sobre los analizadores, consulte [Analizador y analizador](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)de servicios de lenguaje heredado . A <xref:Microsoft.VisualStudio.Package.Colorizer> continuación, la clase marca cada carácter del token con la información de color y devuelve esa información al editor que muestra el archivo de origen.

 La información de color devuelta al editor es un índice en una lista de elementos coloreables. Cada elemento coloreable especifica un valor de color y un conjunto de atributos de fuente, como negrita o tachado. El editor proporciona un conjunto de elementos coloreables predeterminados que el servicio de lenguaje puede usar. Todo lo que necesita hacer es especificar el índice de color adecuado para cada tipo de token. Sin embargo, puede proporcionar un conjunto de elementos coloreables personalizados y los índices que proporcione para los tokens, y hacer referencia a su propia lista de elementos coloreables en lugar de la lista predeterminada. También debe establecer `RequestStockColors` la entrada del Registro en `RequestStockColors` 0 (o no especifique la entrada en absoluto) para admitir colores personalizados. Puede establecer esta entrada del Registro <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> con un parámetro con nombre en el atributo definido por el usuario. Para obtener más información sobre cómo registrar un servicio de lenguaje y establecer sus opciones, consulte [Registro de un servicio](../../extensibility/internals/registering-a-legacy-language-service1.md)de lenguaje heredado .

## <a name="custom-colorable-items"></a>Elementos coloreables personalizados
 Para proporcionar sus propios elementos coloreables personalizados, debe invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> método y <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase. El primer método devuelve el número de elementos coloreables personalizados que admite el servicio de lenguaje y el segundo obtiene el elemento coloreable personalizado por índice. Cree la lista predeterminada de elementos coloreables personalizados. En el constructor de su servicio de lenguaje, todo lo que necesita hacer es proporcionar cada elemento coloreable con un nombre. Visual Studio controla automáticamente el caso en el que el usuario selecciona un conjunto diferente de elementos coloreables. Este nombre es el que aparece en la página de propiedades **Fuentes y colores** del cuadro de diálogo **Opciones** (disponible en el menú **Herramientas** de Visual Studio) y este nombre determina qué color ha reemplazado un usuario. Las opciones del usuario se almacenan en una memoria caché en el registro y se accede por el nombre de color. La página de propiedades **Fuentes y colores** enumera todos los nombres de color en orden alfabético, por lo que puede agrupar los colores personalizados precediendo cada nombre de color con su nombre de idioma; por ejemplo, "**TestLanguage- Comment**" y "**TestLanguage- Keyword**". O puede agrupar los elementos coloreables por tipo, "**Comment (TestLanguage)**" y "**Keyword (TestLanguage)**". Se prefiere agrupar por nombre de idioma.

> [!CAUTION]
> Se recomienda encarecidamente que incluya el nombre del idioma en el nombre del elemento coloreable para evitar colisiones con los nombres de elementos coloreables existentes.

> [!NOTE]
> Si cambia el nombre de uno de los colores durante el desarrollo, debe restablecer la memoria caché que Visual Studio creó la primera vez que se tenía acceso a los colores. Puede hacerlo ejecutando el comando **Restablecer el subárbol experimental** desde el menú del programa SDK de Visual Studio.

 Tenga en cuenta que nunca se hace referencia al primer elemento de la lista de elementos coloreables. Visual Studio siempre proporciona los colores y atributos de texto predeterminados para ese elemento. La forma más fácil de lidiar con esto es proporcionar un elemento coloreable marcador de posición como el primer elemento.

### <a name="high-color-colorable-items"></a>Artículos coloreables de alto color
 Los elementos coloreables también pueden admitir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> valores de color de 24 bits o altos a través de la interfaz. La clase <xref:Microsoft.VisualStudio.Package.ColorableItem> MPF <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> admite la interfaz y los colores de 24 bits se especifican en el constructor junto con los colores normales. Vea la clase <xref:Microsoft.VisualStudio.Package.ColorableItem> para obtener información más detallada. En el ejemplo siguiente se muestra cómo establecer los colores de 24 bits para palabras clave y comentarios. Los colores de 24 bits se utilizan cuando el color de 24 bits se admite en el escritorio del usuario; de lo contrario, se utilizan los colores de texto normales.

 Recuerde, estos son los colores predeterminados para su idioma; el usuario puede cambiar estos colores a lo que quiera.

### <a name="example"></a>Ejemplo
 En este ejemplo se muestra una forma de declarar <xref:Microsoft.VisualStudio.Package.ColorableItem> y rellenar una matriz de elementos coloreables personalizados mediante la clase. En este ejemplo se establecen los colores de palabra clave y comentario utilizando colores de 24 bits.

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

## <a name="the-colorizer-class-and-the-scanner"></a>La clase Colorizer y el Escáner
 La <xref:Microsoft.VisualStudio.Package.LanguageService> clase base <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> tiene un método <xref:Microsoft.VisualStudio.Package.Colorizer> que instantánea la clase. El analizador que se <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> devuelve desde <xref:Microsoft.VisualStudio.Package.Colorizer> el método se pasa al constructor de clase.

 Debe implementar <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> el método en su <xref:Microsoft.VisualStudio.Package.LanguageService> propia versión de la clase. La <xref:Microsoft.VisualStudio.Package.Colorizer> clase utiliza el analizador para obtener toda la información de color del token.

 El analizador debe <xref:Microsoft.VisualStudio.Package.TokenInfo> rellenar una estructura para cada token que encuentre. Esta estructura contiene información como el intervalo que ocupa el token, el índice de color <xref:Microsoft.VisualStudio.Package.TokenTriggers>que se va a usar, qué tipo es el token y los desencadenadores de token (consulte ). Solo el intervalo y el índice de <xref:Microsoft.VisualStudio.Package.Colorizer> color son necesarios para la coloración de la clase.

 El índice de <xref:Microsoft.VisualStudio.Package.TokenInfo> color almacenado en la <xref:Microsoft.VisualStudio.Package.TokenColor> estructura suele ser un valor de la enumeración, que proporciona una serie de índices con nombre correspondientes a varios elementos de lenguaje, como palabras clave y operadores. Si la lista de elementos coloreables personalizados coincide con los elementos presentados en la <xref:Microsoft.VisualStudio.Package.TokenColor> enumeración, puede usar la enumeración como el color para cada token. Sin embargo, si tiene elementos coloreables adicionales o no desea utilizar los valores existentes en ese orden, puede organizar la lista de elementos coloreables personalizados para que se adapte a sus necesidades y devolver el índice adecuado a esa lista. Solo asegúrese de convertir <xref:Microsoft.VisualStudio.Package.TokenColor> el índice en <xref:Microsoft.VisualStudio.Package.TokenInfo> un al almacenarlo en la estructura; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] sólo ve el índice.

### <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo el analizador puede identificar tres tipos de token: números, puntuación e identificadores (cualquier cosa que no sea un número o puntuación). Este ejemplo es solo para fines ilustrativos y no representa una implementación completa del analizador y del analizador. Se supone que hay `Lexer` una `GetNextToken()` clase con un método que devuelve una cadena.

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
- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
- [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)
