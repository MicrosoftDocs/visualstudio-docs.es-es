---
title: "El archivo especificado en Nombre de archivo no es un archivo XML v&#225;lido | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El archivo especificado en Nombre de archivo no es un archivo XML v&#225;lido
El nombre de archivo proporcionado no es un archivo XML válido. Para especificar la estructura permitida y el contenido de un documento XML, puede usar una definición de tipo de documento \(DTD\), un esquema reducido de datos XML \(XDR\) de Microsoft o un esquema de lenguaje de definición de esquema XML \(XSD\). Los esquemas XSD son el método preferido para especificar gramáticas XML en [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  En algunas versiones anteriores de Visual Studio, el **Diseñador XML** era el diseñador de los conjuntos de datos y el esquema XML. El **Diseñador XML** aún puede usarse para crear y editar archivos de esquema XML. Sin embargo, en [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], el diseñador para crear y editar conjuntos de datos es el **Diseñador de Dataset**. Para obtener más información, consulta [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
### Para corregir este error  
  
-   Compruebe que está proporcionando el nombre de archivo correcto.  
  
-   Asegúrese de que el archivo especificado contiene XML válido. Para ello, cargue el archivo XML que desea comprobar en el **Diseñador XML**. En el menú **XML**, haga clic en **Validar datos XML**. Los errores se muestran en la ventana **Lista de tareas**.  
  
-   Si el archivo XML tiene un esquema XML asociado, compruebe que los elementos aparecen en la estructura definida y que el contenido de los elementos individuales se ajusta a los tipos de datos declarados especificados en el esquema.  
  
## Vea también  
 <xref:System.Xml>   
 [Cómo: Analizar rutas de acceso a archivos](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)