---
title: Exposición de tipos a diseñadores visuales Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708436"
---
# <a name="expose-types-to-visual-designers"></a>Exponer tipos a diseñadores visuales
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debe tener acceso a las definiciones de clase y tipo en tiempo de diseño para mostrar un diseñador visual. Las clases se cargan desde un conjunto predefinido de ensamblados que incluyen el conjunto de dependencias completo del proyecto actual (referencias más sus dependencias). También puede ser necesario que los diseñadores visuales accedan a clases y tipos definidos en archivos generados por herramientas personalizadas.

 Los [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemas y los sistemas de proyecto proporcionan compatibilidad para acceder a clases y tipos generados a través de archivos ejecutables portátiles temporales (PE temporales). Cualquier archivo generado por una herramienta personalizada se puede compilar en un ensamblado temporal para que los tipos se puedan cargar desde esos ensamblados y exponerse a los diseñadores. La salida de cada herramienta personalizada se compila en un PE temporal independiente y el éxito o el error de esta compilación temporal depende únicamente de si se puede compilar o no el archivo generado. Aunque un proyecto puede no construirse como un todo, los PE temporales individuales pueden seguir estando disponibles para los diseñadores.

 El sistema de proyectos proporciona compatibilidad completa para realizar el seguimiento de los cambios en el archivo de salida de una herramienta personalizada, siempre que estos cambios sean el resultado de ejecutar la herramienta personalizada. Cada vez que se ejecuta la herramienta personalizada, se genera un nuevo PE temporal y se envían las notificaciones adecuadas a los diseñadores.

> [!NOTE]
> Dado que el archivo de generación ejecutable de programa temporal se produce en segundo plano, no se notifica ningún error al usuario si se produce un error en la compilación.

 Las herramientas personalizadas que aprovechan la compatibilidad temporal con PE deben seguir las siguientes reglas:

- **GeneratesDesignTimeSource** debe establecerse en 1 en el registro.

     Ninguna compilación de archivos ejecutables del programa tiene lugar sin esta configuración.

- El código generado debe estar en el mismo idioma que la configuración del proyecto global.

     El PE temporal se compila independientemente de lo que <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> la herramienta personalizada notifica como la extensión solicitada en siempre que **GeneratesDesignTimeSource** se establece en 1 en el registro. La extensión no necesita ser *.vb*, *.cs*o *.jsl*; puede ser cualquier extensión.

- El código generado por la herramienta personalizada debe ser válido y debe compilarse por sí solo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> utilizando solo el conjunto de referencias presentes en el proyecto en el momento en que finaliza la ejecución.

     Cuando se compila un PE temporal, el único archivo de origen proporcionado al compilador es la salida de la herramienta personalizada. Por lo tanto, una herramienta personalizada que utiliza un PE temporal debe generar archivos de salida que se pueden compilar independientemente de otros archivos del proyecto.

## <a name="see-also"></a>Vea también
- [Introducción al objeto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)
- [Registrar generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)
