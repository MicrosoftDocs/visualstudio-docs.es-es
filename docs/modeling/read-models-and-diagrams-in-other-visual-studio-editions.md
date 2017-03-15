---
title: Leer modelos y diagramas en otras ediciones de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 20
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 9ffc4c39dee2da1d6daa051f478eac18d9670151
ms.lasthandoff: 02/22/2017

---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leer modelos y diagramas en otras ediciones de Visual Studio
Al abrir un modelo en una versión de Visual Studio que no es compatible con la creación de modelos, el modelo se abre en modo de solo lectura. En este modo puede cambiar el diseño de los diagramas pero no se puede cambiar el modelo.  
  
 Para ver qué versiones de Visual Studio admiten la creación de modelos, vea [compatibilidad con la versión de arquitectura y herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Acceder a un modelo y a diagramas  
 Para leer un diagrama de dependencia, debe usar Visual Studio para abrir el proyecto de modelado y, a continuación, abra el diagrama dentro de él.  
  
 Por este motivo, si desea leer un diagrama de dependencia, también debe tener acceso al proyecto de modelado en el que se creó. Puede hacerlo obteniendo acceso a los proyectos desde [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] u obteniendo una copia de los archivos de proyecto.  
  
> [!NOTE]
>  Esto no se aplica a los mapas de código ni a los diagramas de clases .NET generados a partir del código. Esos diagramas pueden verse sin necesidad de un proyecto de modelado.  
  
 Para leer un diagrama de dependencia, el conjunto mínimo de archivos que necesita es el siguiente:  
  
-   Los dos archivos de diagrama que desea leer, por ejemplo, diagrama **MyDiagram.classdiagram y MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Diagramas de dependencia, también debe tener el archivo que se denomina *MyDiagram***. layerdiagram.suppressions**.  
  
-   El modelado de archivo de proyecto (**MyModel.modelproj**)  
  
-   El archivo del modelo raíz (**ModelDefinition\MyModel. UML**)  
  
-   Los archivos del paquete de cualquier paquete que se hace referencia en el diagrama (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Cambios que puede realizar en modo de solo lectura  
 Si abre un modelo y sus diagramas en una versión de Visual Studio que no es compatible con la creación de modelos, no podrá cambiar el modelo. Es decir, no podrá cambiar los elementos y relaciones que se muestran en los diagramas o en el explorador de modelos. Sin embargo, puede realizar algunos cambios en el diseño de los diagramas:  
  
-   Reorganizar las formas y conectores del diagrama.  
  
-   Expandir y contraer formas.  
  
 Puede guardar estos cambios. Si desea realizar los cambios visibles para otros usuarios, debe enviar al menos actualizada **. Layout** archivos.  
  
##  <a name="a-namerelatedtopicsa-related-topics"></a><a name="RelatedTopics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)|Un diagrama de capas muestra la estructura de una arquitectura existente o propuesta. Cuando se escribe código, se puede validar automáticamente con un diagrama de capas.|  
  
## <a name="see-also"></a>Vea también  
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
