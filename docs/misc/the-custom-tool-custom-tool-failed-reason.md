---
title: "The custom tool &#39;custom tool&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.generator_fail_errorinfo"
ms.assetid: e846b946-a123-49fe-b4bc-a7bbda501417
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The custom tool &#39;custom tool&#39; failed. &lt;reason&gt;
La herramienta personalizada no se ejecutó correctamente.  
  
 Si detecta un error de MSDataSetGenerator al actualizar proyectos que contienen conjuntos de datos de n niveles, deberá volver a ejecutar la herramienta personalizada una vez actualizados todos los proyectos.  
  
 Error de la herramienta personalizada 'MSDataSetGenerator'.  El proyecto especificado en el atributo DataSetProject de \<nombre del conjunto de datos\> debe tener como destino una versión de .NET Framework igual o posterior a la del proyecto actual.  
  
### Para corregir los errores de MSDataSetGenerator en conjuntos de datos de n niveles  
  
-   En el Explorador de soluciones, haga clic con el botón secundario del mouse en el archivo .xsd y, a continuación, haga clic en **Ejecutar herramienta personalizada**.