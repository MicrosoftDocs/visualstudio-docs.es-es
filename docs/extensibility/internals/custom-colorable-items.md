---
title: Elementos coloreables personalizados | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b23ff39abcb9a1354ea28becab3b7df867378ddf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133377"
---
# <a name="custom-colorable-items"></a>Elementos coloreables personalizados
Puede invalidar la lista de tipos para colorear, como palabras clave y los comentarios, mediante la implementación de elementos coloreables personalizados como parte de su servicio de lenguaje.  
  
## <a name="user-settings-of-colorable-items"></a>Configuración de usuario de elementos coloreables  
 Puede mostrar el **fuentes y colores** cuadro de diálogo seleccionando **opciones** en el **herramientas** menú y, a continuación, seleccione **fuentes y colores** en **entorno**. Cuando selecciona una presentación, como **Editor de texto** o **ventana de comandos**, **mostrar elementos** cuadro de lista muestra todos los elementos coloreables para que se muestran. Puede ver y cambiar la fuente, el tamaño, el color de primer plano y el color de fondo de cada elemento coloreable. Las opciones se almacenan en una memoria caché en el registro y se tiene acceso con el nombre del elemento coloreable.  
  
## <a name="presentation-of-colorable-items"></a>Presentación de elementos coloreables  
 Dado que el IDE controla los reemplazos de usuario de coloreables elementos en el **fuentes y colores** cuadro de diálogo, debe proporcionar solo cada elemento coloreable personalizado con un nombre. Este nombre es lo que aparece en el **mostrar elementos** lista. Los elementos coloreables aparecen en orden alfabético. Para agrupar elementos coloreable personalizado de su servicio de lenguaje, puede comenzar cada nombre con el nombre del lenguaje, por ejemplo **NewLanguage - comentario** y **NewLanguage - palabra clave**.  
  
> [!CAUTION]
>  Debe incluir el nombre del idioma en el nombre del elemento coloreable para evitar conflictos con los nombres de elemento coloreable existentes. Si cambia el nombre de uno de los elementos coloreables durante el desarrollo, debe restablecer la memoria caché que se creó la primera vez que se tiene acceso a los elementos coloreables. Puede restablecer la memoria caché experimental con la herramienta CreateExpInstance, que se instala con el SDK de Visual Studio, normalmente se encuentra en el directorio  
>   
>  **C:\Program archivos (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Para restablecer la memoria caché, llame a `CreateExpInstance /Reset`. Para obtener más información sobre CreateExpInstance, consulte [CreateExpInstance utilidad](../../extensibility/internals/createexpinstance-utility.md).  
  
 El primer elemento en la lista de elementos coloreables nunca se hace referencia. El primer elemento corresponde a un índice de elemento coloreable de 0, y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siempre proporciona los colores predeterminados de texto y los atributos de ese elemento. La manera más fácil de tratar este elemento sin referencia es proporcionar un elemento coloreable de marcador de posición en la lista como el primer elemento.  
  
## <a name="implementing-custom-colorable-items"></a>Implementar elementos coloreables personalizados  
  
1.  Definir lo que debe colorea en su idioma, por ejemplo, palabra clave, operador e identificador.  
  
2.  Cree una enumeración de estos elementos coloreables.  
  
3.  Asocie los tipos de token devueltos desde un analizador o un escáner con los valores enumerados.  
  
     Por ejemplo, los valores que representan los tipos de token podrían ser los mismos valores en la enumeración de elementos coloreable personalizado.  
  
4.  En la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método en su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> de objetos, rellenar la lista de atributos con los valores de la enumeración de elementos coloreable personalizado correspondientes a los tipos de token devueltos desde el analizador o un escáner.  
  
5.  En la misma clase que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz, implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaz y sus dos métodos, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implementar la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7.  Si desea admitir valores de color de 24 bits o alta, también implementan la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz.  
  
8.  En el objeto de servicio de lenguaje, crear una lista que contiene su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objetos, uno para cada elemento coloreable puede identificar el analizador o un escáner.  
  
     Puede tener acceso a cada elemento de la lista mediante el valor correspondiente de la enumeración de elementos coloreable personalizado. Utilice los valores de enumeración como un índice en la lista. Nunca se tiene acceso el primer elemento de la lista, ya que se corresponde con el texto predeterminado de estilo que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siempre controla propio. Es posible compensar esto mediante la inserción de un elemento coloreable de marcador de posición al principio de la lista.  
  
9. En la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> (método), devuelve el número de elementos de la lista de elementos coloreable personalizado.  
  
10. En la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> (método), devuelven el elemento coloreable solicitado de la lista.  
  
 Para obtener un ejemplo de cómo implementar el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaces, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Vea también  
 [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Sintaxis de color en los editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Color de un servicio de lenguaje heredado sintaxis](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Color de la sintaxis de implementación](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Uso de elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)