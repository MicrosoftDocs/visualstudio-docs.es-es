---
title: "Creaci&#243;n de vistas de lista de tareas personalizadas | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lista de tareas, vistas personalizadas"
ms.assetid: c25f8f5d-55a1-4b5e-b617-3d1140bcb98a
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Creaci&#243;n de vistas de lista de tareas personalizadas
Puede mostrar una lista de tareas personalizado en Visual Studio creando una vista de lista de la tarea personalizada.  
  
 Utilice el registro para crear una vista personalizada y crear estas especificaciones:  
  
-   las columnas  
  
-   El criterio de ordenación de las columnas  
  
-   el criterio de ordenación predeterminado  
  
-   Categorías de tareas que desea mostrar  
  
 Puede mostrar una categoría personalizada o especificar CAT\_ALL para varias categorías.  También puede crear columnas personalizadas de texto que contienen cualquier texto.  Sin embargo, no puede ordenar en columnas personalizadas de texto.  
  
 Las tablas siguientes muestran el formato registro en las vistas de lista de la tarea personalizada.  
  
 En cada una de las tablas, *VS la raíz del registro* es igual a HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio \\ 8,0 \\.  Las tablas proporcionan las entradas de script y la información adicional para cada instrucción del registro.  
  
 \[*VS la raíz del registro*\\TaskList\\Views \\*GUID*\]  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|---------------|-----------------|  
|Name|REG\_SZ|Text|Nombre de cadena de la vista o de \#xxx.<br /><br /> El nombre puede ser una cadena normal como “mi vista personalizada” o una cadena de recursos dentro de un paquete \(\#xxx\).|  
|Paquete|REG\_SZ|Text|\[\] opte representación de cadena del GUID.  Esto es necesario si algunas cadenas son cadenas de recursos \(\#xxx\); si no, se omite.|  
  
 \[*VS la raíz del registro*\\TaskList\\Views \\*GUID*\\Columns \\*número*\]  
  
> [!NOTE]
>  *número* es el orden basado en una de las columnas en la vista \(donde la columna situada más a la izquierda 1\).  Para obtener más columnas, incremento *número*.  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|---------------|-----------------|  
|Campo|REG\_DWORD||<xref:Microsoft.VisualStudio.Shell.Interop.VSTASKFIELD> que es el campo de la columna.|  
|Ancho|REG\_DWORD||Opcional.  Ancho de la columna en píxeles.  si la columna no es importante, se omite este parámetro.|  
|Índice|REG\_DWORD||Opcional.  Si el campo es FLD\_CUSTOM, es el índice de columna personalizado.|  
|Name|REG\_SZ|Text|si el campo es FLD\_CUSTOM, éste es el nombre de la columna personalizada.<br /><br /> El nombre también puede ser una cadena de recursos en formato de \#xxx.|  
|Filtro|REG\_SZ o REG\_DWORD||Cualquier DWORD que tiene una cuenta integrada VSTASKCATEGORY o una STRING que representa el GUID de una categoría personalizada.|  
  
 \[*VS la raíz del registro*\\TaskList\\Views \\*GUID*\\Sort \\*número*\]  
  
> [!NOTE]
>  *número* identifica el criterio de ordenación.  Por ejemplo, para el primer criterio de orden, igual a 1. de *número* .  Para el segundo criterio de orden, *número* equivale a 2, y así sucesivamente.  
  
|Name|Tipo|Intervalo|Descripción|  
|----------|----------|---------------|-----------------|  
|Campo|REG\_DWORD||<xref:Microsoft.VisualStudio.Shell.Interop.VSTASKFIELD> que es el campo de la columna.|  
|Índice|REG\_DWORD||Opcional.  Si el campo es FLD\_CUSTOM, es el índice de columna personalizado.|  
  
 Para implementar una columna personalizada, debe implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2> en los elementos de tarea y debe implementar los métodos siguientes en esa interfaz:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.get_CustomColumnText%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.put_CustomColumnText%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.IsCustomColumnReadOnly%2A>  
  
 Cuando sea necesario, las consultas de la lista de tareas la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2> mediante un número de columnas personalizado de una vista concreta, representada por *algún guid*.  Si la tarea tiene la información adecuada sobre esa columna en esa vista, se proporciona información a esa columna, y especifica si el texto es de solo lectura.  
  
## Vea también  
 [Cómo: crear categorías personalizadas de listas de tareas](../misc/how-to-create-custom-categories-of-task-lists.md)