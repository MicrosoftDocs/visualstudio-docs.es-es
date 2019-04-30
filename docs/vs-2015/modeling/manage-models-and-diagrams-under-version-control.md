---
title: Administrar modelos y diagramas con control de versiones | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4c29b7e3279513e2876396abd5083c3ddefa0baf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440942"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Administrar modelos y diagramas con control de versiones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Administre distintas versiones de los diagramas y proyectos de modelado, incluidos los mapas de código (archivos .dgml), con el [control de versiones de Team Foundation o Git](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314); ya sea localmente con Team Foundation Server o en la nube con Visual Studio Team Services.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!IMPORTANT]
> Sea prudente cuando varios usuarios trabajen en el mismo proyecto de modelado. Descubra cómo puede [organizar modelos en proyectos grandes o medianos](../modeling/structure-your-modeling-solution.md).  
  
## <a name="ModelingProjects"></a> Archivos en un proyecto de modelado  
 En un proyecto de modelado pueden trabajar varios usuarios al mismo tiempo, siempre que lo hagan en archivos diferentes.  
  
 Para evitar o resolver conflictos entre los cambios realizados por diferentes usuarios, es importante comprender cómo se almacena el modelo en los archivos.  
  
- Cada paquete se almacena en un archivo **.uml** independiente, que se guarda en la carpeta del proyecto **ModelDefinition** . El modelo también tiene un archivo **.uml** . Si uno de estos archivos se elimina o se daña, se perderá el paquete o modelo correspondiente.  
  
- Cada diagrama se almacena en dos archivos. Por ejemplo, un diagrama de clases contiene lo siguiente:  
  
    - **DiagramName.classdiagram** : si este archivo se elimina o daña, se perderá el diagrama, pero las clases y asociaciones que se mostraban seguirán estando en el modelo y se podrán ver en el Explorador de modelos UML.  
  
    - **DiagramName.classdiagram.layout** : si se elimina este archivo, las formas seguirán apareciendo en el diagrama, pero perderán sus tamaños y posiciones. Cada archivo de diseño depende de un archivo de diagrama. Para verlo, haga clic en [+] junto al archivo de diagrama en el Explorador de soluciones.  
  
> [!NOTE]
> Es importante mantener la coherencia entre los archivos. Por ejemplo, si se usa control de código fuente para revertir los cambios en un archivo .uml, al mismo tiempo se deben deshacer los cambios correspondientes en los archivos .*diagram y .layout. Los elementos representados en una. \*archivo de diagrama se perderá si no se representan también en un archivo .uml.  
  
## <a name="Shared"></a> Trabajar en proyectos de modelado compartidos  
 Para minimizar los conflictos al trabajar simultáneamente en diferentes partes de un proyecto:  
  
- Divida el proyecto de modelado en paquetes que representen las distintas áreas de trabajo. Mueva todo el modelo a los paquetes, en lugar de dejarlo en el modelo raíz. Para obtener más información, consulte [definir paquetes y espacios de nombres](../modeling/define-packages-and-namespaces.md).  
  
- No puede haber varios usuarios trabajando de forma simultánea en el mismo paquete o diagrama.  
  
- Si está usando perfiles, asegúrese de que todos los usuarios tengan los mismos perfiles instalados. Consulte [personalizar el modelo con perfiles y estereotipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
- Para asegurarse de que solo cambia el paquete en el que está trabajando:  
  
    - Establezca la propiedad **LinkedPackage** de un diagrama de casos de uso, componente o clase UML.  
  
    - En el Explorador de modelos UML, arrastre una actividad o interacción al paquete en cuanto la cree. Este elemento aparecerá en el Explorador de modelos UML cuando cree el primer nodo en el diagrama de actividades o de secuencia.  
  
- Para facilitar el seguimiento de los paquetes, cambie el nombre de los archivos de paquete de manera que reflejen los nombres reales de los paquetes.  
  
- En [!INCLUDE[esprscc](../includes/esprscc-md.md)], realice siempre las operaciones **Proteger** y **Obtener última versión** en el proyecto de modelado completo; nunca en archivos individuales.  
  
- Realice siempre una operación **Get** justo antes de proteger el proyecto de modelado.  
  
- Cierre siempre todos los diagramas antes de realizar una operación **Get** .  
  
    > [!NOTE]
    > Si un archivo está abierto cuando se realiza una operación **Get**y la operación da como resultado cambios locales, se le pedirá que vuelva a cargar el archivo. En este caso, haga clic en **No**y, después, vuelva a cargar el proyecto completo. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto de modelado, haga clic en **Descargar el proyecto**y, luego, haga clic en **Volver a cargar el proyecto**.  
  
### <a name="Exclusive"></a> Cambios que requieren acceso exclusivo al modelo  
 Antes de realizar los siguientes tipos de cambios, asegúrese de que tiene un bloqueo de desprotección en todo el proyecto.  
  
- Eliminar o cambiar el nombre de elementos a los que se hace referencia desde otros paquetes.  
  
- Cambiar las propiedades de relaciones que cruzan los límites del paquete.  
  
- Si quiere saber más sobre los bloqueos de desprotección, consulte [Desproteger y editar archivos](http://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).  
  
##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Para mover un archivo de diagrama dentro o fuera de una carpeta de proyecto  
  
1. Abra el **Símbolo del sistema para desarrolladores de Visual Studio**.  
  
2. Use **tf rename** para mover el archivo de diagrama y su archivo **.layout** :  
  
     `tf rename sourcePath targetPath`  
  
3. En el Explorador de soluciones, haga clic con el botón derecho en el archivo y, después, haga clic en **Excluir del proyecto**.  
  
4. Agregue el archivo a la carpeta de destino.  
  
     En el Explorador de soluciones, haga clic con el botón derecho en la carpeta de destino o en el proyecto, apunte a **Agregar**y, después, haga clic en **Elemento existente**. En el cuadro de diálogo, seleccione el archivo de diagrama y, después, haga clic en **Agregar**. El archivo de diseño se agregará automáticamente.  
  
    > [!NOTE]
    > No se puede mover el archivo a un proyecto diferente.  
  
## <a name="Merging"></a> Combinar los cambios en los archivos de modelo y diagramas  
 Después de que varios usuarios trabajen en un modelo al mismo tiempo, [!INCLUDE[esprscc](../includes/esprscc-md.md)] le solicitará que combine los cambios en los archivos de modelo. Si se trabaja en proyectos independientes, tal como se describe en las secciones anteriores, se evitarán la mayoría de combinaciones. Normalmente, los conflictos restantes se pueden combinar automáticamente de forma segura. Los siguientes tipos de cambios no deberían causar ninguna dificultad:  
  
- Tipos de líneas de vida. Cuando se agrega una línea de vida a una interacción (diagrama de secuencia), su tipo se almacena en el modelo raíz, a menos que la línea de vida se crease a partir de un tipo existente.  
  
- Las actividades e interacciones nuevas se almacenan inicialmente en el modelo raíz.  
  
- Agregar elementos y relaciones.  
  
- Eliminar o cambiar el nombre de elementos a los que únicamente se hace referencia desde su propio paquete.  
  
## <a name="see-also"></a>Vea también  
 [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)   
 [Compartir modelos y exportar diagramas](../modeling/share-models-and-exporting-diagrams.md)
