---
title: Elementos coloreables personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708994"
---
# <a name="custom-colorable-items"></a>Elementos coloreables personalizados
Puede invalidar la lista de tipos de coloración, como palabras clave y comentarios, mediante la implementación de elementos coloreables personalizados como parte del servicio de lenguaje.

## <a name="user-settings-of-colorable-items"></a>Configuración de usuario de elementos coloreables
 Para mostrar el cuadro de diálogo **fuentes y colores** , seleccione **Opciones** en el menú **herramientas** y, a continuación, seleccione **fuentes y colores** en **entorno**. Al seleccionar una pantalla, como editor de **texto** o **ventana de comandos**, el cuadro de lista **Mostrar elementos** muestra todos los elementos coloreables de la pantalla. Puede ver y cambiar la fuente, el tamaño, el color de primer plano y el color de fondo de cada elemento coloreable. Las opciones se almacenan en una memoria caché en el registro y se obtiene acceso a ellas mediante el nombre del elemento coloreable.

## <a name="presentation-of-colorable-items"></a>Presentación de elementos coloreables
 Dado que el IDE controla invalidaciones de usuario de elementos coloreables en el cuadro de diálogo **fuentes y colores** , solo necesita proporcionar un nombre a cada elemento coloreable personalizado. Este nombre es lo que aparece en la lista **Mostrar elementos** . Los elementos coloreables aparecen en orden alfabético. Para agrupar los elementos coloreables personalizados del servicio de lenguaje, puede empezar cada nombre con su nombre de idioma, por ejemplo **NewLanguage-comment** y **NewLanguage-keyword**.

> [!CAUTION]
> Debe incluir el nombre de idioma en el nombre del elemento coloreable para evitar colisiones con los nombres de elementos coloreables existentes. Si cambia el nombre de uno de los elementos coloreables durante el desarrollo, debe restablecer la memoria caché que se creó la primera vez que se obtuvo acceso a los elementos coloreables. Puede restablecer la memoria caché experimental con la herramienta **CreateExpInstance** , que se instala con el SDK de Visual Studio, normalmente en el directorio:
>
> *C:\Archivos de programa (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Para restablecer la memoria caché, escriba **CreateExpInstance/RESET**. Para obtener más información sobre **CreateExpInstance**, consulte la [utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).

 Nunca se hace referencia al primer elemento de la lista de elementos coloreables. El primer elemento corresponde a un índice de elemento coloreable de 0, y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siempre proporciona los colores de texto y los atributos predeterminados para ese elemento. La manera más sencilla de tratar con este elemento sin referencia es proporcionar un elemento coloreable de marcador de posición en la lista como primer elemento.

## <a name="implement-custom-colorable-items"></a>Implementar elementos coloreables personalizados

1. Defina lo que se debe colorear en el idioma, por ejemplo, palabra clave, operador y identificador.

2. Cree una enumeración de estos elementos coloreables.

3. Asociar los tipos de token devueltos de un analizador o un escáner con los valores enumerados.

    Por ejemplo, los valores que representan los tipos de token pueden ser los mismos que en la enumeración de elementos coloreables personalizados.

4. En la implementación del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> objeto, rellene la lista de atributos con los valores de la enumeración de elementos coloreables personalizados correspondientes a los tipos de token devueltos desde el analizador o el escáner.

5. En la misma clase que implementa la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaz, implemente la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaz y sus dos métodos, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Si desea admitir valores de color de 24 bits o alto, implemente también la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaz.

8. En el objeto de servicio de lenguaje, cree una lista que contenga los <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objetos, uno para cada elemento coloreable que pueda identificar el analizador o el escáner.

    Puede tener acceso a cada elemento de la lista mediante el valor correspondiente de la enumeración de elementos coloreables personalizados. Utilice los valores de enumeración como un índice en la lista. Nunca se tiene acceso al primer elemento de la lista, ya que corresponde al estilo de texto predeterminado que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siempre se controla. Puede compensar esto mediante la inserción de un elemento de marcador de posición en el principio de la lista.

9. En la implementación del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método, devuelva el número de elementos de la lista elementos coloreables personalizados.

10. En la implementación del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método, devuelva el elemento coloreable solicitado de la lista.

    Para obtener un ejemplo de cómo implementar las <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaces y, vea <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>Vea también
- [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Colores de la sintaxis en editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Color de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementar el color de la sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)
- [Cómo: usar elementos coloreables integrados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
