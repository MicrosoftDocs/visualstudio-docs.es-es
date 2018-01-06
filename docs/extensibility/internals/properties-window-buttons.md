---
title: Botones de la ventana de propiedades | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 950b9f0a7b0f38689042877a42499e23253e6486
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-buttons"></a>Botones de la ventana de propiedades
Según el lenguaje de desarrollo y el tipo de producto, se muestran algunos botones de forma predeterminada en la barra de herramientas para el **propiedades** ventana. En todos los casos, el **por categorías**, **Alphabetized**, **propiedades**, y **páginas de propiedades** se muestran los botones. En Visual C# y Visual Basic, la **eventos** también se muestra el botón. En determinados proyectos de Visual C++, el **VC ++ mensajes** y **VC invalida** se muestran los botones. Botones adicionales pueden mostrarse para otros tipos de proyecto. Para obtener más información acerca de los botones en la **propiedades** ventana, consulte [ventana propiedades](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementación de botones de la ventana de propiedades  
 Al hacer clic en el **por categorías** button, llamadas de Visual Studio la <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfaz en el objeto que tiene el foco para ordenar sus propiedades por categoría. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>se implementa en el `IDispatch` objeto que se enviará a la **propiedades** ventana.  
  
 Hay 11 categorías de propiedad predefinida, que tienen valores negativos. Puede definir categorías personalizadas, pero se recomienda asignarles valores positivos para distinguirlas de las categorías predefinidas.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> método devuelve el valor de la categoría de propiedades adecuado para la propiedad especificada. El <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> método devuelve una cadena que contiene el nombre de categoría. Sólo tendrá que proporcionar soporte técnico para los valores de categoría personalizada ya que Visual Studio conoce los valores de categoría de propiedad estándar.  
  
 Al hacer clic en el **Alphabetized** botón, las propiedades se muestran en orden alfabético por nombre. Los nombres se recuperan mediante `IDispatch` según un algoritmo de ordenación localizado.  
  
 Cuando el **propiedades** ventana está abierta, la **propiedades** botón se muestra automáticamente como seleccionado. En otras partes del entorno, se muestra el mismo botón y hacer clic en él para mostrar el **propiedades** ventana.  
  
 El **páginas de propiedades** botón no está disponible si `ISpecifyPropertyPages` no está implementado para el objeto seleccionado. Propiedades dependientes de la configuración de presentación que suelen estar asociadas con soluciones y proyectos de páginas de propiedades, pero pueden ser también estar asociadas con elementos de proyecto (por ejemplo, en Visual C++).  
  
> [!NOTE]
>  No se puede agregar botones de barra de herramientas para el **propiedades** ventana y con código no administrado. Para agregar un botón de barra de herramientas, debe crear un objeto administrado que se deriva de <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Vea también  
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)