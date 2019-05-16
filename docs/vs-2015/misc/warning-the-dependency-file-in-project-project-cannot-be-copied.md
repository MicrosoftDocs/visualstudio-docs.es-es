---
title: 'Advertencia: la dependencia &#39;archivo&#39; proyecto &#39;proyecto&#39; no se puede copiar en el directorio de ejecución porque sobrescribiría la referencia &#39;archivo. &#39; | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8865a1509016a51f30913e51c06e2bcc63912013
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694245"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Advertencia: la dependencia &#39;archivo&#39; proyecto &#39;proyecto&#39; no se puede copiar en el directorio de ejecución porque sobrescribiría la referencia &#39;archivo.&#39;
Existe un conflicto entre dependencias; para que la aplicación se ejecute se debería copiar más de un archivo de ensamblado distinto con el mismo nombre en el directorio bin. El directorio de ejecución puede resolver el conflicto, ya que una de las dependencias es una referencia principal.  
  
 Para ir al nodo de referencia principal en conflicto, haga doble clic en este elemento Lista de tareas.  
  
 Esta advertencia se produce cuando hay un conflicto de dependencias que se ha solucionado al agregar una de las dependencias en conflicto como referencia. O bien es posible que tuviera una referencia de versión 1 y luego agregara una segunda referencia que hiciera referencia a la versión 2 de la primera referencia.  
  
 Es decir, este error se produce porque los proyectos de la solución tienen referencias entre sí, pero las referencias se crearon como referencias de archivo (mediante el botón **Examinar** del cuadro de diálogo [Agregar referencia](https://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) ), en lugar de como referencias de proyecto a proyecto (mediante la pestaña **Proyecto** del cuadro de diálogo **Agregar referencia** ). La ventaja de una referencia de proyecto a proyecto es que crea una dependencia entre los proyectos en el sistema de compilación de modo que el proyecto dependiente se compilará si ha cambiado desde la última vez que se compiló el proyecto al que hace referencia. Una referencia a un archivo no crea una dependencia de compilación, por lo que es posible compilar el proyecto al que hace referencia sin compilar el proyecto dependiente y la referencia puede quedar obsoleta; un proyecto puede hacer referencia a una versión compilada previamente del proyecto. Esto puede dar lugar a que se necesiten varias versiones de un solo archivo DLL en el directorio bin, lo cual no es posible y da lugar a este mensaje de error.  
  
 Este mensaje aparece cada vez que hay un conflicto en el directorio bin y es posible que la aplicación no funcione correctamente. Aunque es posible que haya solucionado este problema, esta advertencia seguirá apareciendo porque el sistema del proyecto no puede determinar si la versión de una dependencia funcionará correctamente con todos los componentes.  
  
 **Para corregir este error**  
  
- Copie un archivo de ensamblado (o ninguno) en el directorio bin, lo que se puede hacer colocando los archivos de ensamblado en la memoria caché global de ensamblados. La memoria caché global de ensamblados soluciona los conflictos de nombre de archivo. No se realizarán copias locales del archivo de ensamblado, porque Common Language Runtime sabe cómo buscar ensamblados en la memoria caché global de ensamblados. Para obtener más información, vea [Working with Assemblies and the Global Assembly Cache](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) y [Error: the dependency 'file' in project 'project' cannot be copied to the run directory because it would conflict with dependency 'file'](/visualstudio/misc/error-dependency-file?view=vs-2015).  
  
## <a name="see-also"></a>Vea también  
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)   
 [Caché global de ensamblados](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Cómo: Creación y eliminación de dependencias del proyecto](../ide/how-to-create-and-remove-project-dependencies.md)