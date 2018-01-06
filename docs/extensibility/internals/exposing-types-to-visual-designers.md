---
title: "Exponer tipos de diseñadores visuales | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a85648a95a6651ff62f50b2361b07feba9a58b47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-types-to-visual-designers"></a>Exponer tipos de diseñadores visuales
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debe tener acceso a definiciones de clase y tipo en tiempo de diseño para mostrar un diseñador visual. Las clases se cargan desde un conjunto predefinido de ensamblados que incluyen el conjunto completo de dependencia del proyecto actual (referencias y sus dependencias). También puede ser necesario a los diseñadores visuales para tener acceso a clases y tipos que se definen en archivos generados por herramientas personalizadas.  
  
 El [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemas del proyecto proporcionan compatibilidad para tener acceso a las clases generadas y los tipos a través de portable temporal archivos ejecutables (PEs temporal). Cualquier archivo generado por una herramienta personalizada se puede compilar en un ensamblado temporal para que pueden cargar desde esos ensamblados y expone a los diseñadores de tipos. El resultado de cada herramienta personalizada se compila en un archivo PE temporal independiente, y el éxito o error de esta compilación temporal depende solo si no se puede compilar el archivo generado. Aunque no puede compilar un proyecto como un todo, archivos PE temporales individual pueden disponible para los diseñadores.  
  
 El sistema del proyecto proporciona compatibilidad completa para el seguimiento de cambios en el archivo de salida de una herramienta personalizada, siempre que estos cambios son el resultado de ejecutar la herramienta personalizada. Cada vez que se ejecuta la herramienta personalizada, se genera un nuevo archivo PE temporal y se envían las notificaciones adecuadas para los diseñadores.  
  
> [!NOTE]
>  Como archivo ejecutable de generación de programas temporales se realiza en segundo plano, errores no se notifican al usuario si se produce un error en la compilación.  
  
 Herramientas personalizadas que aprovechan las ventajas del soporte de PE temporal deben seguir las reglas siguientes:  
  
-   `GeneratesDesignTimeSource`debe establecerse en 1 en el registro.  
  
     Ninguna compilación del archivo ejecutable de programa tiene lugar sin esta configuración.  
  
-   El código generado debe estar en el mismo idioma que la configuración global de proyectos.  
  
     El archivo PE temporal se compila sin tener en cuenta que la herramienta personalizada que se notifica como la extensión solicitada en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> siempre que `GeneratesDesignTimeSource` está establecido en 1 en el registro. La extensión no necesita ser .vb, .cs o .jsl; puede ser cualquier extensión.  
  
-   El código generado por la herramienta personalizada debe ser válido y debe compilar en su propio con solo el conjunto de referencias en el proyecto en el momento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> termina de ejecutarse.  
  
     Cuando se compila un archivo PE temporal, el único archivo de origen proporcionado para el compilador es el resultado de la herramienta personalizada. Por lo tanto, una herramienta personalizada que utiliza un archivo PE temporal debe generar archivos de salida que se pueden compilar independientemente de otros archivos en el proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Introducción al objeto BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)   
 [Registro de generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)