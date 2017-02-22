---
title: "Botones de la ventana de propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ventana de propiedades, botones"
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Botones de la ventana de propiedades
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dependiendo del lenguaje de desarrollo y del tipo de producto, algunos botones se muestran de forma predeterminada en la barra de herramientas de la ventana de **Propiedades** .  En todos los casos, se muestran **Clasificadas**, **alfabetizado**, botones de **Propiedades**, y de **Páginas de propiedades** .  En Visual c\# y Visual Basic, el botón eventos también se muestra.  En determinados proyectos de Visual C\+\+, se muestran **mensajes de VC\+\+** y botones de **VC reemplaza** .  Los botones adicionales se pueden mostrar para otros tipos de proyecto.  Para obtener más información sobre los botones de la ventana de **Propiedades** , vea [Ventana Propiedades](../../ide/reference/properties-window.md).  
  
## implementación de los botones de la ventana Propiedades  
 Al hacer clic en el botón de **Clasificadas** , Visual Studio denomina interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> en el objeto que tiene el foco para ordenar las propiedades por categoría.  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> se implementa en el objeto de `IDispatch` que aparece en la ventana de **Propiedades** .  
  
 Hay 11 categorías de propiedades predefinidas, que tienen valores negativos.  Puede definir categorías personalizadas, pero se recomienda las asignar valores positivos para distinguirlas de las categorías predefinidas.  
  
 El método de <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> devuelve el valor apropiado de la categoría de propiedad para la propiedad especificada.  El método de <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> devuelve una cadena que contiene el nombre de categoría.  Tiene que proporcionar solo compatibilidad con valores personalizados de la categoría porque Visual Studio conoce los valores estándar de la categoría de la propiedad.  
  
 Al hacer clic en el botón de **alfabetizado** , las propiedades se muestran en orden alfabético por nombre.  los nombres son recuperados por `IDispatch` según un algoritmo de ordenación localizado.  
  
 Cuando la ventana de **Propiedades** está abierto, el botón de **Propiedades** automáticamente se muestra como seleccionado.  En otras partes del entorno, se muestra el mismo botón, y puede hacer clic para mostrar la ventana de **Propiedades** .  
  
 El botón de **Páginas de propiedades** no está disponible si `ISpecifyPropertyPages` no se implementa para el objeto seleccionado.  Las páginas de propiedades muestran propiedades dependientes que son normalmente asociado con soluciones y proyectos, pero pueden estar también están asociados con los elementos de proyecto \(por ejemplo, en Visual C\+\+\).  
  
> [!NOTE]
>  No puede agregar botones de la barra de herramientas en la ventana de **Propiedades** mediante código no administrado.  Para agregar un botón de la barra de herramientas, debe crear un objeto que deriva de <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## Vea también  
 [Extender propiedades](../../extensibility/internals/extending-properties.md)