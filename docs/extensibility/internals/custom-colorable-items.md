---
title: Artículos coloreables personalizados ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708994"
---
# <a name="custom-colorable-items"></a>Artículos coloreables personalizados
Puede invalidar la lista de tipos para colorear, como palabras clave y comentarios, implementando elementos coloreables personalizados como parte del servicio de lenguaje.

## <a name="user-settings-of-colorable-items"></a>Configuración de usuario de elementos coloreables
 Puede mostrar el cuadro de diálogo **Fuentes y colores** seleccionando **Opciones** en el menú **Herramientas** y, a continuación, seleccionando Fuentes **y colores** en **Entorno**. Al seleccionar una visualización, como **Editor** de texto o Ventana de **comandos**, el cuadro de lista **Mostrar elementos** muestra todos los elementos coloreables para esa visualización. Puede ver y cambiar la fuente, el tamaño, el color de primer plano y el color de fondo de cada elemento coloreable. Las opciones se almacenan en una memoria caché en el registro y se accede a ellas mediante el nombre del elemento coloreable.

## <a name="presentation-of-colorable-items"></a>Presentación de artículos coloreables
 Dado que el IDE controla las invalidaciones de usuario de elementos coloreables en el fuentes **y colores** cuadro de diálogo, solo necesita proporcionar cada elemento coloreable personalizado con un nombre. Este nombre es el que aparece en la lista **Mostrar elementos.** Los elementos coloreables aparecen en orden alfabético. Para agrupar los elementos coloreables personalizados de su servicio de lenguaje, puede comenzar cada nombre con su nombre de idioma, por ejemplo **NewLanguage - Comment** y **NewLanguage - Keyword**.

> [!CAUTION]
> Debe incluir el nombre del idioma en el nombre del elemento coloreable para evitar colisiones con los nombres de elementos coloreables existentes. Si cambia el nombre de uno de los elementos coloreables durante el desarrollo, debe restablecer la memoria caché que se creó la primera vez que se tuvo acceso a los elementos coloreables. Puede restablecer la memoria caché experimental con la herramienta **CreateExpInstance,** que se instala con el SDK de Visual Studio, normalmente en el directorio:
>
> *C:-Archivos de programa (x86)-Microsoft Visual Studio 14.0-VSSDK-VisualStudioIntegration-Tools-Bin*
>
> Para restablecer la memoria caché, escriba **CreateExpInstance /Reset**. Para obtener más información acerca de **CreateExpInstance**, vea [CreateExpInstance utility](../../extensibility/internals/createexpinstance-utility.md).

 Nunca se hace referencia al primer elemento de la lista de elementos coloreables. El primer elemento corresponde a un índice de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elemento coloreable de 0 y siempre proporciona los colores y atributos de texto predeterminados para ese elemento. La forma más fácil de tratar con este elemento sin referencia es proporcionar un elemento coloreable marcador de posición en su lista como el primer elemento.

## <a name="implement-custom-colorable-items"></a>Implementar elementos coloreables personalizados

1. Defina lo que se debe colorear en su idioma, por ejemplo Palabra clave, Operador e Identificador.

2. Cree una enumeración de estos elementos coloreables.

3. Asocie los tipos de token devueltos desde un analizador o analizador con los valores enumerados.

    Por ejemplo, los valores que representan los tipos de token podrían ser los mismos valores en la enumeración de elementos coloreables personalizados.

4. En la implementación del método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> objeto, rellene la lista de atributos con los valores de la enumeración de elementos coloreables personalizados correspondientes a los tipos de token devueltos desde el analizador o el analizador.

5. En la misma clase <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> que implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> la interfaz, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>la interfaz y sus dos métodos, y .

6. Implemente la interfaz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Si desea admitir valores de color de 24 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> bits o altos, implemente también la interfaz.

8. En el objeto de servicio de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> lenguaje, cree una lista que contenga los objetos, una para cada elemento coloreable que el analizador o el analizador pueda identificar.

    Puede tener acceso a cada elemento de la lista mediante el valor correspondiente de la enumeración de elementos coloreables personalizados. Utilice los valores de enumeración como un índice en la lista. Nunca se tiene acceso al primer elemento de la lista, porque corresponde al estilo de texto predeterminado que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siempre se controla a sí mismo. Puede compensar esto insertando un elemento coloreable de marcador de posición al principio de la lista.

9. En la implementación del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> método, devuelva el número de elementos de la lista de elementos coloreables personalizados.

10. En la implementación del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> método, devuelva el elemento coloreable solicitado de la lista.

    Para obtener un ejemplo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> cómo implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>las interfaces y, consulte .

## <a name="see-also"></a>Vea también
- [Modelo de un servicio de lenguaje heredado](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Coloración de sintaxis en editores personalizados](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Coloreación de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementar coloración de sintaxis](../../extensibility/internals/implementing-syntax-coloring.md)
- [Cómo: Usar elementos coloreables incorporados](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
