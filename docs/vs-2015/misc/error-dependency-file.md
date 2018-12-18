---
title: 'Error: la dependencia &#39;archivo&#39; proyecto &#39;proyecto&#39; no se puede copiar en el directorio de ejecución porque entraría en conflicto con la dependencia &#39;archivo&#39; | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4edf474cd67d21833743891eeeb75ce09decb87e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751938"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Error: la dependencia &#39;archivo&#39; proyecto &#39;proyecto&#39; no se puede copiar en el directorio de ejecución porque entraría en conflicto con la dependencia &#39;archivo&#39;
Existe un conflicto entre referencias; se está copiando más de una dependencia distinta con el mismo nombre de archivo en el directorio bin para que la aplicación se ejecute. El directorio de ejecución no puede resolver el conflicto porque ninguna de las dependencias es una referencia principal.  
  
 Este error impedirá que la compilación se lleve a cabo.  
  
 Haga doble clic en este elemento de lista de tareas para ir al nodo de referencias del proyecto en el que se ha producido el conflicto.  
  
 **Para corregir este error**  
  
-   Convierta uno de los ensamblados en una referencia directa del proyecto. Un posible inconveniente de este método es que no está garantizado que el ensamblado que elija funcione con los ensamblados que pueden requerir alguna otra versión del ensamblado al que se hace referencia.  
  
     \- o -  
  
-   Procure que ambas copias del ensamblado tengan nombres seguros y estén en la memoria caché global de ensamblados. Así, no será necesario copiar los ensamblados en el directorio bin.  
  
## <a name="see-also"></a>Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [Caché global de ensamblados](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Ensamblados con nombre seguro](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Versiones de los ensamblados](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [Cómo: Crear y quitar dependencias del proyecto](../ide/how-to-create-and-remove-project-dependencies.md)