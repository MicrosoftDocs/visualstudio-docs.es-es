---
title: "Opciones, editor de texto, XAML, formato | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing"
helpviewer_keywords: 
  - "espaciado de elementos, configuración de vista XAML"
  - "espaciado de atributos, configuración de vista XAML"
  - "configuración de vista XAML, eventos de formato automático"
  - "eventos de formato automático, configuración de vista XAML"
  - "configuración de vista XAML, ajuste de etiquetas"
  - "configuración de vista XAML, inserción automática"
  - "estilo de comillas, configuración de vista XAML"
  - "formato XAML, WPF Designer"
  - "configuración de vista XAML, cuadro de herramientas"
  - "configuración de vista XAML, espaciado de elementos"
  - "vista predeterminada, configuración de vista XAML"
  - "inserción automática, configuración de vista XAML"
  - "configuración de vista XAML, vista predeterminada"
  - "configuración de vista XAML, estilo de comillas"
  - "ajuste de etiquetas, configuración de vista XAML"
  - "WPF Designer, formato XAML"
  - "configuración de vista XAML, espaciado de atributos"
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones, editor de texto, XAML, formato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice la página de propiedades **Formato** para especificar cómo se da formato a los elementos y atributos en los documentos XAML.  Para abrir el cuadro de diálogo **Opciones**, haga clic en el menú **Herramientas** y, a continuación, en **Opciones**.  Para obtener acceso a la página de propiedades **Formato**, expanda el nodo **Editor de texto**, **XAML**, **Formato**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Eventos de formato automático  
 El formato automático puede producirse cuando se detecta cualquiera de los siguientes eventos.  
  
-   Completar una etiqueta de cierre o una etiqueta sencilla.  
  
-   Completar una etiqueta inicial.  
  
-   Pegar desde el Portapapeles.  
  
-   Dar formato a los comandos de teclado.  
  
 Puede especificar qué eventos originan el formato automático.  
  
|||  
|-|-|  
|**Al completarse la etiqueta de cierre o etiqueta sencilla**|El formato automático se produce cuando termina de escribir una etiqueta de cierre o una etiqueta sencilla.  Una etiqueta sencilla no tiene atributos, por ejemplo `<Button />`.|  
|**Al completar la etiqueta de inicio**|El formato automático se produce cuando termina de escribir una etiqueta de inicio.|  
|**Al pegar desde el Portapapeles**|El formato automático se produce al pegar XAML del Portapapeles en la vista XAML.|  
  
## Estilo de comillas  
 Este valor indica si los valores de atributo se escriben entre comillas sencillas o dobles.  Tanto el autoformateador como la finalización automática de IntelliSense utilizan este valor.  
  
 Una vez establecida esta opción, sólo afectará a los atributos agregados posteriormente mediante el diseñador o de forma manual en la vista XAML.  
  
|||  
|-|-|  
|**Comillas dobles \("\)**|Los valores de atributo se escriben entre comillas dobles.<br /><br /> `<Button Name="button1">Hello</Button>`|  
|**Comillas sencillas \('\)**|Los valores de atributo se escriben entre comillas sencillas.<br /><br /> `<Button Name='button1'>Hello</Button>`|  
  
## Ajuste de etiquetas  
 Puede especificar una longitud de línea para el ajuste de etiquetas.  Cuando se habilita el ajuste de etiquetas, cualquier elemento XAML agregado posteriormente mediante el diseñador se ajustará adecuadamente.  
  
|||  
|-|-|  
|**Ajustar etiquetas que superan la longitud especificada**|Especifica si las líneas se ajustan a la longitud de línea especificada por **Longitud**.|  
|**Longitud**|El número de caracteres que puede contener una línea.  Si es necesario, algunas líneas de XAML pueden superar la longitud de línea especificada.|  
  
## Espaciado de atributos  
 Utilice este valor para controlar cómo se organizan los atributos en el documento XAML.  
  
|||  
|-|-|  
|**Mantener líneas nuevas y espacios entre atributos**|Las líneas nuevas y los espacios entre los atributos no se ven afectados por el formato automático.<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Insertar un espacio entre atributos**|Los atributos ocupan una línea y los atributos adyacentes se separan por un espacio.  Se aplica la configuración de ajuste de etiquetas.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|  
|**Poner cada atributo en una línea diferente**|Cada atributo ocupa su propia línea.  Esto resulta útil cuando hay muchos atributos.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**Poner el primer atributo en la misma línea que la etiqueta de inicio**|Cuando se activa, el primer atributo aparece en la misma línea que la etiqueta de inicio del elemento.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
  
## Espaciado de elementos  
 Utilice este valor para controlar cómo se organizan los elementos en el documento XAML.  
  
|||  
|-|-|  
|**Mantener líneas nuevas en el contenido**|No se quitan las líneas vacías del contenido del elemento.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Contraer varias líneas vacías del contenido en una sola línea**|Las líneas vacías del contenido del elemento se contraen en una sola línea.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**Quitar líneas vacías en el contenido**|Se quitan todas las líneas vacías del contenido del elemento.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`|  
  
## Inserción automática  
 Utilice este valor para controlar cuándo se generan etiquetas y comillas automáticamente.  
  
|||  
|-|-|  
|**Etiquetas de cierre**|Especifica si se genera automáticamente una etiqueta de cierre de un elemento al cerrar la etiqueta de apertura con el carácter mayor que \(\>\).|  
|**Comillas de atributo**|Especifica si se generan comillas cuando se selecciona un valor de atributo en la lista desplegable de finalización de instrucciones.|  
|**Llaves de cierre de MarkupExtensions**|Especifica si se genera automáticamente la llave de cierre de una extensión de marcado \(}\) al escribir el carácter de llave de apertura \({\).|  
|**Comas para separar los parámetros MarkupExtension**|Especifica si se generan comas al escribir más de un parámetro en una extensión de marcado.|  
  
## Vista predeterminada  
 Utilice este valor para controlar si aparece la vista Diseño al cargar documentos XAML.  
  
|||  
|-|-|  
|**Abrir siempre los documentos en la vista XAML completa**|Especifica si los documentos XAML sólo aparecen en la vista XAML y no en la vista Diseño.  Es útil para cargar documentos grandes.|  
  
## Cuadro de herramientas  
 Utilice este valor para especificar si los controles de usuario y los controles personalizados se muestran en el Cuadro de herramientas.  
  
|||  
|-|-|  
|**Rellenar automáticamente los elementos del cuadro de herramientas**|Especifica si los controles de usuario y los controles personalizados de la solución actual se muestran automáticamente en el Cuadro de herramientas.|  
  
## Vea también  
 [XAML en WPF](../Topic/XAML%20in%20WPF.md)   
 [Cómo: Cambiar la configuración de la vista XAML](http://msdn.microsoft.com/es-es/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [Tutoriales para el uso de XAML y código](http://msdn.microsoft.com/es-es/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)