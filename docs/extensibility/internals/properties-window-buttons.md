---
title: Botones de la ventana Propiedades (Properties Window Buttons) Microsoft Docs
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
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706170"
---
# <a name="properties-window-buttons"></a>Botones de la ventana Propiedades
Según el idioma de desarrollo y el tipo de producto, algunos botones se muestran de forma predeterminada en la barra de herramientas de la ventana **Propiedades.** En todos los casos, se muestran los botones **Clasificado**, **Alfabetizado**, **Propiedades**y **Páginas** de propiedades. También se muestra el botón **Eventos** en Visual C. y Visual Basic. En determinados proyectos de Visual C++, se muestran los botones **Vc++ Messages** y **VC Overrides.** Es posible que se muestren botones adicionales para otros tipos de proyecto. Para obtener más información acerca de los botones de la ventana **Propiedades,** vea [Ventana Propiedades](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementación de botones de ventana de propiedades
 Al hacer clic en el **botón Clasificado,** Visual Studio llama a la <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfaz en el objeto que tiene el foco para ordenar sus propiedades por categoría. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>se implementa en `IDispatch` el objeto que se presenta en la ventana **Propiedades.**

 Hay 11 categorías de propiedades predefinidas, que tienen valores negativos. Puede definir categorías personalizadas, pero le recomendamos que les asigne valores positivos para distinguirlas de las categorías predefinidas.

 El <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> método devuelve el valor de categoría de propiedad adecuado para la propiedad especificada. El <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> método devuelve una cadena que contiene el nombre de categoría. Solo tiene que proporcionar compatibilidad con los valores de categoría personalizados porque Visual Studio conoce los valores de categoría de propiedad estándar.

 Al hacer clic en el botón **Alphabetized,** las propiedades se muestran en orden alfabético por nombre. Los nombres se `IDispatch` recuperan según un algoritmo de ordenación localizado.

 Cuando la ventana **Propiedades** está abierta, el botón **Propiedades** se muestra automáticamente como seleccionado. En otras partes del entorno, se muestra el mismo botón y puede hacer clic en él para mostrar la ventana **Propiedades.**

 El botón **Páginas** `ISpecifyPropertyPages` de propiedades no está disponible si no se implementa para el objeto seleccionado. Las páginas de propiedades muestran propiedades dependientes de la configuración que normalmente están asociadas con soluciones y proyectos, pero también se pueden asociar a elementos de proyecto (por ejemplo, en Visual C++).

> [!NOTE]
> No puede agregar botones de barra de herramientas a la ventana **Propiedades** mediante código no administrado. Para agregar un botón de barra de herramientas, debe crear un objeto administrado que derive de <xref:System.Windows.Forms.Design.PropertyTab>.

## <a name="see-also"></a>Vea también
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
