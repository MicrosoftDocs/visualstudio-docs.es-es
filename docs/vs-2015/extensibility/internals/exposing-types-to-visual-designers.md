---
title: Exposición de tipos a los diseñadores visuales | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d6c0e163b751f1873fdb941e85c273dcc4fde5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691205"
---
# <a name="exposing-types-to-visual-designers"></a>Exposición de tipos a diseñadores visuales
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debe tener acceso a las definiciones de clase y tipo en tiempo de diseño para mostrar un diseñador visual. Las clases se cargan desde un conjunto predefinido de ensamblados que incluyen el conjunto completo de dependencias del proyecto actual (las referencias y sus dependencias). También puede ser necesario para los diseñadores visuales para tener acceso a clases y tipos que se definen en los archivos generados por herramientas personalizadas.  
  
 El [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../../includes/csprcs-md.md)] sistemas del proyecto proporcionan soporte técnico para acceder a las clases generadas y los tipos a través de portable temporal archivos ejecutables (PE temporales). Cualquier archivo generado por una herramienta personalizada puede compilarse en un ensamblado temporal para que se pueden cargar desde esos ensamblados y expone a los diseñadores de tipos. La salida de cada herramienta personalizada se compila en un archivo PE temporal independiente y el éxito o fracaso de esta compilación temporal depende solo si se puede compilar el archivo generado. Aunque no puede compilar un proyecto como un todo, PE temporales individual es posible que siga estando disponible para diseñadores.  
  
 El sistema del proyecto proporciona compatibilidad completa para el seguimiento de cambios en el archivo de salida de una herramienta personalizada, siempre que estos cambios son el resultado de ejecutar la herramienta personalizada. Cada vez que se ejecuta la herramienta personalizada, se genera un nuevo archivo PE temporal y se envían las notificaciones adecuadas a los diseñadores.  
  
> [!NOTE]
> Como archivo ejecutable de generación de programas temporales se realiza en segundo plano, errores no se notifican al usuario si se produce un error en la compilación.  
  
 Herramientas personalizadas para aprovechan las ventajas de soporte técnico de PE temporal deben seguir las reglas siguientes:  
  
- `GeneratesDesignTimeSource` debe establecerse en 1 en el registro.  
  
     Compilación de ningún archivo ejecutable del programa tiene lugar sin esta configuración.  
  
- El código generado debe estar en el mismo idioma que la configuración global de proyectos.  
  
     El archivo PE temporal se compila sin tener en cuenta que la herramienta personalizada que se notifica como la extensión solicitada en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> siempre que `GeneratesDesignTimeSource` está establecido en 1 en el registro. La extensión no necesita ser .jsl; .cs o .vb puede ser cualquier extensión.  
  
- El código generado por la herramienta personalizada debe ser válido y debe compilar en su propio usando solo el conjunto de referencias en el proyecto en el momento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> termina de ejecutarse.  
  
     Cuando se compila un archivo PE temporal, el único archivo de origen proporcionado para el compilador es el resultado de la herramienta personalizada. Por lo tanto, una herramienta personalizada que utiliza un archivo PE temporal debe generar los archivos de salida que se pueden compilar independientemente de otros archivos en el proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Introducción al objeto BuildManager](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)   
 [Determinar el Namespace predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Registro de generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)
