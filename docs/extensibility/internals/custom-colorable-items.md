---
title: Elementos coloreables personalizados | Microsoft Docs
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
ms.openlocfilehash: 037cd62bea7051e8341101a888bd428b7f78e828
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878809"
---
# <a name="custom-colorable-items"></a>Elementos coloreables personalizados
Puede reemplazar la lista de tipos para colorear, como palabras clave y los comentarios, mediante la implementación de elementos coloreables personalizados como parte de su servicio de lenguaje.  
  
## <a name="user-settings-of-colorable-items"></a>Configuración de usuario de elementos coloreables  
 Puede mostrar el **fuentes y colores** cuadro de diálogo seleccionando **opciones** en el **herramientas** menú y, a continuación, seleccione **fuentes y colores** en **entorno**. Cuando selecciona una presentación, como **Editor de texto** o **ventana de comandos**, el **mostrar elementos** cuadro de lista muestra todos los elementos coloreables para que se muestran. Puede ver y cambiar la fuente, tamaño, color de primer plano y color de fondo de cada elemento coloreable. Las opciones se almacenan en una caché en el registro y acceder con el nombre del elemento coloreable.  
  
## <a name="presentation-of-colorable-items"></a>Presentación de elementos coloreables  
 Dado que el IDE controla los reemplazos de elementos coloreables en el **fuentes y colores** cuadro de diálogo, debe proporcionar solo cada elemento coloreable personalizado con un nombre. Este nombre es lo que aparece en el **mostrar elementos** lista. Los elementos coloreables aparecen en orden alfabético. Para agrupar elementos coloreables personalizados de su servicio lenguaje, puede comenzar cada nombre con el nombre del lenguaje, por ejemplo **NewLanguage - comentario** y **NewLanguage - palabra clave**.  
  
> [!CAUTION]
>  Debe incluir el nombre del idioma en el nombre del elemento coloreable para evitar conflictos con otros nombres de elemento coloreable. Si cambia el nombre de uno de los elementos coloreables durante el desarrollo, debe restablecer la memoria caché que se creó la primera vez que se tuvo acceso a los elementos coloreables. Puede restablecer la memoria caché experimental con los **CreateExpInstance** herramienta, que se instala con el SDK de Visual Studio, normalmente en el directorio:  
>   
>  *C:\Program archivos (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>   
>  Para restablecer la memoria caché, escriba **CreateExpInstance /Reset**. Para obtener más información acerca de **CreateExpInstance**, consulte [utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 El primer elemento en la lista de elementos coloreables nunca se hace referencia. El primer elemento corresponde a un índice del elemento coloreable de 0, y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siempre proporciona los colores de texto predeterminado y atributos para ese elemento. La manera más fácil de tratar con este elemento sin referencia es proporcionar un elemento coloreable de marcador de posición en la lista como el primer elemento.  
  
## <a name="implement-custom-colorable-items"></a>Implementar elementos coloreables personalizados  
  
1. Definir lo que debe se coloreará en su idioma, por ejemplo, palabra clave, operador e identificador.  
  
2. Crear una enumeración de estos elementos coloreables.  
  
3. Asociar los tipos de token devueltos por un analizador o un escáner con los valores enumerados.  
  
    Por ejemplo, los valores que representan los tipos de token podrían ser los mismos valores en la enumeración de elementos coloreables personalizados.  
  
4. En la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método en su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> de objetos, rellenar la lista de atributos con los valores de la enumeración de elementos coloreables personalizados correspondientes a los tipos de token devueltos desde el analizador o un escáner.  
  
5. En la misma clase que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz, implemente el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaz y sus dos métodos, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6. Implementar la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7. Si desea admitir valores de color de 24 bits o alta, también implementan la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz.  
  
8. En el objeto de servicio de lenguaje, cree una lista que contiene su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objetos, uno para cada elemento coloreable que se puede identificar el escáner o el analizador.  
  
    Puede tener acceso a cada elemento de la lista con el valor correspondiente de la enumeración de elementos coloreables personalizados. Usar los valores de enumeración como un índice en la lista. Nunca se tiene acceso el primer elemento en la lista, ya que se corresponde con el texto predeterminado de estilo que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siempre controla propio. Es posible compensar esto mediante la inserción de un elemento coloreable de marcador de posición al principio de la lista.  
  
9. En la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método, devuelve el número de elementos de la lista de elementos coloreables personalizados.  
  
10. En la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método, devolver el elemento coloreable solicitado de la lista.  
  
    Para obtener un ejemplo de cómo implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaces, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Vea también  
 [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Colores de sintaxis en editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Colores de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Color de la sintaxis de implementación](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Cómo: usar elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)