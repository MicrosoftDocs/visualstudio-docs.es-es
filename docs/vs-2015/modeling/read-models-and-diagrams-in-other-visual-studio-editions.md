---
title: Leer modelos y diagramas en otras ediciones de Visual Studio | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c02e700eaa17f29726d9e3ddee83bfbc4874fdda
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988812"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Leer modelos y diagramas en otras ediciones de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al abrir un modelo en una versión de Visual Studio que no es compatible con la creación de modelos, el modelo se abre en modo de solo lectura. En este modo puede cambiar el diseño de los diagramas pero no se puede cambiar el modelo.  
  
 Para ver qué versiones de Visual Studio admite la creación de modelos, vea [compatibilidad con la versión de arquitectura y las herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Acceder a un modelo y a diagramas  
 Para leer un diagrama UML o un diagrama de capas, debe usar Visual Studio para abrir el proyecto de modelado y, a continuación, abra el diagrama dentro de él.  
  
 Por este motivo, si desea leer un diagrama UML o un diagrama de capas, también debe tener acceso al proyecto de modelado en el que se creó. Puede hacerlo obteniendo acceso a los proyectos desde [!INCLUDE[esprscc](../includes/esprscc-md.md)] u obteniendo una copia de los archivos de proyecto.  
  
> [!NOTE]
>  Esto no se aplica a los mapas de código ni a los diagramas de clases .NET generados a partir del código. Esos diagramas pueden verse sin necesidad de un proyecto de modelado.  
  
 Para leer un diagrama UML o un diagrama de capas, necesita el siguiente conjunto mínimo de archivos:  
  
-   Los dos archivos de diagrama que desea leer, por ejemplo, de diagrama **MyDiagram.classdiagram y MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Diagramas de capas, también debe tener el archivo que se denomina _MyDiagram_**. layerdiagram.suppressions**.  
  
-   El modelado del archivo de proyecto (**MyModel.modelproj**)  
  
-   El archivo de modelo raíz (**ModelDefinition\MyModel. UML**)  
  
-   Los archivos del paquete para los paquetes que se hace referencia en el diagrama (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Cambios que puede realizar en modo de solo lectura  
 Si abre un modelo y sus diagramas en una versión de Visual Studio que no es compatible con la creación de modelos, no podrá cambiar el modelo. Es decir, no podrá cambiar los elementos y relaciones que se muestran en los diagramas o en el explorador de modelos. Sin embargo, puede realizar algunos cambios en el diseño de los diagramas:  
  
- Reorganizar las formas y conectores del diagrama.  
  
- Expandir y contraer formas.  
  
  Puede guardar estos cambios. Si desea que los cambios sea visible para otros usuarios, debe enviar al menos la actualización **.layout** archivos.  
  
##  <a name="RelatedTopics"></a> Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md)|Un diagrama de capas muestra la estructura de una arquitectura existente o propuesta. Cuando se escribe código, se puede validar automáticamente con un diagrama de capas.|  
|[Diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md)|Un diagrama de actividad muestra un flujo de trabajo, ya sea en un proceso empresarial o en software.|  
|[Diagrama de clases de UML: referencia](../modeling/uml-class-diagrams-reference.md)|Un diagrama de clase muestra tipos y relaciones que se usan en muchos contextos, como el código, los esquemas de base de datos, los protocolos de comunicaciones o el glosario de términos usados para describir un dominio empresarial.|  
|[Diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md)|Un diagrama de componentes muestra partes que se pueden separar en un diseño de software y sus interfaces.|  
|[Diagramas de secuencia de UML: referencia](../modeling/uml-sequence-diagrams-reference.md)|Un diagrama de secuencia muestra las interacciones entre los elementos de un diseño de software.|  
|[Diagramas de casos de uso UML: referencia](../modeling/uml-use-case-diagrams-reference.md)|Un diagrama de casos de uso muestra los usuarios de un sistema y las actividades que pueden realizar para lograr objetivos concretos.|  
  
## <a name="see-also"></a>Vea también  
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
