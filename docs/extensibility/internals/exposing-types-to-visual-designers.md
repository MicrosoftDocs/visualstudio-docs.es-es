---
title: Exponer tipos a diseñadores visuales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708436"
---
# <a name="expose-types-to-visual-designers"></a>Exponer tipos a diseñadores visuales
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe tener acceso a las definiciones de clase y de tipo en tiempo de diseño para poder mostrar un diseñador visual. Las clases se cargan desde un conjunto predefinido de ensamblados que incluyen el conjunto de dependencias completo del proyecto actual (referencias más sus dependencias). También puede ser necesario que los diseñadores visuales tengan acceso a clases y tipos definidos en archivos generados por herramientas personalizadas.

 Los [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemas de proyectos de y [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proporcionan compatibilidad para tener acceso a clases y tipos generados a través de archivos ejecutables portables temporales (PES temporales). Cualquier archivo generado por una herramienta personalizada se puede compilar en un ensamblado temporal para que los tipos puedan cargarse desde esos ensamblados y exponerse a los diseñadores. La salida de cada herramienta personalizada se compila en un archivo PE temporal independiente y el éxito o el error de esta compilación temporal depende solo de si se puede compilar o no el archivo generado. Aunque un proyecto no se puede compilar como un todo, el PE temporal individual puede seguir estando disponible para los diseñadores.

 El sistema del proyecto proporciona compatibilidad completa para realizar el seguimiento de los cambios en el archivo de salida de una herramienta personalizada, siempre que estos cambios sean el resultado de la ejecución de la herramienta personalizada. Cada vez que se ejecuta la herramienta personalizada, se genera un nuevo PE temporal y se envían las notificaciones correspondientes a los diseñadores.

> [!NOTE]
> Dado que el archivo temporal de generación de archivos ejecutables se produce en segundo plano, no se envía ningún error al usuario si se produce un error en la compilación.

 Las herramientas personalizadas que aprovechan la compatibilidad temporal con PE deben cumplir las siguientes reglas:

- **GeneratesDesignTimeSource** debe establecerse en 1 en el registro.

     No se realiza ninguna compilación de archivos ejecutables de programa sin esta configuración.

- El código generado debe estar en el mismo idioma que la configuración global del proyecto.

     El PE temporal se compila con independencia de lo que la herramienta personalizada notifique como la extensión solicitada en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> siempre que **GeneratesDesignTimeSource** esté establecido en 1 en el registro. No es necesario que la extensión sea *. VB*, *. CS*o *. jsl*; puede ser cualquier extensión.

- El código generado por la herramienta personalizada debe ser válido y debe compilarse por sí solo usando el conjunto de referencias presentes en el proyecto en el momento en que <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> finaliza la ejecución.

     Cuando se compila un PE temporal, el único archivo de código fuente proporcionado al compilador es la salida de la herramienta personalizada. Por lo tanto, una herramienta personalizada que utiliza un archivo PE temporal debe generar archivos de salida que se pueden compilar de forma independiente de otros archivos del proyecto.

## <a name="see-also"></a>Consulte también
- [Introducción al objeto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)
- [Registro de generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)
