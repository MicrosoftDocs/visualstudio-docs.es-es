---
title: Botones de ventana Propiedades | Microsoft Docs
description: Obtenga información sobre los botones que se muestran de forma predeterminada en la barra de herramientas ventana Propiedades y sobre la implementación de los botones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c45d6cf0f271683c3c708bd71ef46377a5c5ca
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903455"
---
# <a name="properties-window-buttons"></a>Botones de la ventana Propiedades
Según el idioma de desarrollo y el tipo de producto, determinados botones se muestran de forma predeterminada en la barra de herramientas de la **ventana** Propiedades. En todos los casos, se muestran los botones **Categorizado**, **Alfabético,** **Propiedades** y Páginas **de** propiedades. En Visual C# y Visual Basic, **también** se muestra el botón Eventos. En determinados Visual C++ proyectos, se muestran los botones **Mensajes de VC++** y Invalidaciones de **VC.** Se pueden mostrar botones adicionales para otros tipos de proyecto. Para obtener más información sobre los botones de la **ventana** Propiedades, vea [Ventana Propiedades](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementación de botones de ventana Propiedades
 Al hacer clic en **el botón Categorizado,** Visual Studio llama a la interfaz en el objeto que tiene el foco para <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> ordenar sus propiedades por categoría. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> se implementa en el `IDispatch` objeto que se presenta en la **ventana** Propiedades.

 Hay 11 categorías de propiedades predefinidas que tienen valores negativos. Puede definir categorías personalizadas, pero se recomienda asignarles valores positivos para distinguirlas de las categorías predefinidas.

 El <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> método devuelve el valor de categoría de propiedad adecuado para la propiedad especificada. El <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> método devuelve una cadena que contiene el nombre de categoría. Solo tiene que proporcionar compatibilidad con valores de categoría personalizados porque Visual Studio los valores de categoría de propiedad estándar.

 Al hacer clic en el **botón Alfabético,** las propiedades se muestran en orden alfabético por nombre. Los nombres los recupera según `IDispatch` un algoritmo de ordenación localizado.

 Cuando la **ventana** Propiedades está abierta, el **botón Propiedades** se muestra automáticamente como seleccionado. En otras partes del entorno, se muestra el mismo botón y puede hacer clic en él para mostrar la **ventana** Propiedades.

 El **botón Páginas de** propiedades no está disponible si no se implementa para el objeto `ISpecifyPropertyPages` seleccionado. Las páginas de propiedades muestran propiedades dependientes de la configuración que normalmente están asociadas a soluciones y proyectos, pero también se pueden asociar a elementos de proyecto (por ejemplo, en Visual C++).

> [!NOTE]
> No se pueden agregar botones de barra de herramientas a la **ventana** Propiedades mediante código no administrado. Para agregar un botón de barra de herramientas, debe crear un objeto administrado que derive de <xref:System.Windows.Forms.Design.PropertyTab> .

## <a name="see-also"></a>Consulta también
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
