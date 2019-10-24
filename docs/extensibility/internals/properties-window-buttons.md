---
title: Botones de la ventana Propiedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2a41917a58a6fc5780b62c2c9e3db8aa52d407
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725271"
---
# <a name="properties-window-buttons"></a>Botones de la ventana Propiedades
En función del lenguaje de desarrollo y del tipo de producto, se muestran determinados botones de forma predeterminada en la barra de herramientas de la ventana **propiedades** . En todos los casos, se muestran los botones **clasificado**, en **orden alfabético**, **propiedades**y **páginas de propiedades** . En Visual C# y Visual Basic, también se muestra el botón **eventos** . En algunos proyectos C++ visuales, se muestran los botones **mensajes de VC + +** y **VC invalidaciones** . Se pueden mostrar botones adicionales para otros tipos de proyecto. Para obtener más información acerca de los botones de la ventana **propiedades** , vea [ventana Propiedades](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Botones de la ventana de la implementación de propiedades
 Al hacer clic en el botón por **categorías** , Visual Studio llama a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> en el objeto que tiene el foco para ordenar sus propiedades por categoría. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> se implementa en el `IDispatch` objeto que se muestra en la ventana **propiedades** .

 Hay 11 categorías de propiedades predefinidas, que tienen valores negativos. Puede definir categorías personalizadas, pero se recomienda asignarlas valores positivos para distinguirlas de las categorías predefinidas.

 El método <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> devuelve el valor de categoría de propiedad adecuado para la propiedad especificada. El método <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> devuelve una cadena que contiene el nombre de la categoría. Solo tiene que proporcionar compatibilidad con los valores de categoría personalizados porque Visual Studio conoce los valores de categoría de propiedades estándar.

 Al hacer clic en el botón **alfabético** , las propiedades se muestran en orden alfabético por nombre. @No__t_0 recupera los nombres según un algoritmo de ordenación adaptado.

 Cuando la ventana **propiedades** está abierta, el botón **propiedades** se muestra automáticamente como seleccionado. En otras partes del entorno, se muestra el mismo botón y puede hacer clic en él para mostrar la ventana **propiedades** .

 El botón **páginas de propiedades** no está disponible si no se ha implementado `ISpecifyPropertyPages` para el objeto seleccionado. Las páginas de propiedades muestran propiedades dependientes de la configuración que normalmente están asociadas a soluciones y proyectos, pero también se pueden asociar a elementos de proyecto ( C++por ejemplo, en visual).

> [!NOTE]
> No se pueden agregar botones de barra de herramientas a la ventana **propiedades** mediante código no administrado. Para agregar un botón de barra de herramientas, debe crear un objeto administrado que se derive de <xref:System.Windows.Forms.Design.PropertyTab>.

## <a name="see-also"></a>Vea también
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)