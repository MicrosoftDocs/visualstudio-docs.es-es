---
title: Botones de la ventana Propiedades | Microsoft Docs
description: Obtenga información acerca de los botones que se muestran de forma predeterminada en la barra de herramientas para el ventana Propiedades y sobre la implementación de los botones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e99c362904bc40a2937c030f1ee2bb1c4d32a113
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878019"
---
# <a name="properties-window-buttons"></a>Botones de la ventana Propiedades
En función del lenguaje de desarrollo y del tipo de producto, se muestran determinados botones de forma predeterminada en la barra de herramientas de la ventana **propiedades** . En todos los casos, se muestran los botones **clasificado**, en **orden alfabético**, **propiedades** y **páginas de propiedades** . En Visual C# y Visual Basic, también se muestra el botón **eventos** . En algunos proyectos de Visual C++, se muestran los botones **mensajes de VC + +** y **VC invalidaciones** . Se pueden mostrar botones adicionales para otros tipos de proyecto. Para obtener más información acerca de los botones de la ventana **propiedades** , vea [ventana Propiedades](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Botones de la ventana de la implementación de propiedades
 Al hacer clic en el botón por **categorías** , Visual Studio llama a la <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfaz en el objeto que tiene el foco para ordenar sus propiedades por categoría. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> se implementa en el `IDispatch` objeto que se muestra en la ventana **propiedades** .

 Hay 11 categorías de propiedades predefinidas, que tienen valores negativos. Puede definir categorías personalizadas, pero se recomienda asignarlas valores positivos para distinguirlas de las categorías predefinidas.

 El <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> método devuelve el valor de categoría de propiedad adecuado para la propiedad especificada. El <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> método devuelve una cadena que contiene el nombre de la categoría. Solo tiene que proporcionar compatibilidad con los valores de categoría personalizados porque Visual Studio conoce los valores de categoría de propiedades estándar.

 Al hacer clic en el botón **alfabético** , las propiedades se muestran en orden alfabético por nombre. Los nombres se recuperan `IDispatch` según un algoritmo de ordenación adaptado.

 Cuando la ventana **propiedades** está abierta, el botón **propiedades** se muestra automáticamente como seleccionado. En otras partes del entorno, se muestra el mismo botón y puede hacer clic en él para mostrar la ventana **propiedades** .

 El botón **páginas de propiedades** no está disponible si `ISpecifyPropertyPages` no está implementado para el objeto seleccionado. Las páginas de propiedades muestran propiedades dependientes de la configuración que normalmente están asociadas a soluciones y proyectos, pero también se pueden asociar a elementos de proyecto (por ejemplo, en Visual C++).

> [!NOTE]
> No se pueden agregar botones de barra de herramientas a la ventana **propiedades** mediante código no administrado. Para agregar un botón de barra de herramientas, debe crear un objeto administrado que se derive de <xref:System.Windows.Forms.Design.PropertyTab> .

## <a name="see-also"></a>Consulte también
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
