---
title: Editar y continuar (Visual Basic) | Documentos de Microsoft
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa3b8c287129c164d8c6984ac52375d6012fbd68
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471049"
---
# <a name="edit-and-continue-visual-basic"></a>Editar y continuar (Visual Basic)
Editar y continuar es una característica de depuración de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que le permite realizar cambios en el código mientras se ejecuta en modo de interrupción. Una vez que se aplican los cambios de código, se puede reanudar su ejecución con las nuevas modificaciones en contexto y observar el efecto.  
  
 Es posible utilizar la característica Editar y continuar cada vez que se entra en el modo de interrupción. En el modo de interrupción, el puntero de instrucción, una flecha amarilla en la ventana de código fuente, señala la línea que contiene una instrucción ejecutable de un cuerpo de método o propiedad que ejecuta el siguiente.

 Editar y continuar admite la mayoría de los cambios que podría realizar durante una sesión de depuración, pero existen algunas excepciones. Para obtener más información, consulte [cambios admitidos en el código (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Cuando se realiza una modificación que no está autorizada, el cambio se marca con un subrayado ondulado de color púrpura y aparece una tarea en la Lista de tareas. Si desea seguir utilizando Editar y continuar, debe deshacer el cambio no autorizado. Es posible que algunas modificaciones no autorizadas puedan realizarse fuera de Editar y continuar. Si desea retener los resultados de dicha modificación no autorizada, deberá detener la depuración y reiniciar la aplicación.  
  
 Editar y continuar se admite en aplicaciones de x86 y x64 que tienen como destino .NET Framework 4.6 y aplicaciones UWP para Windows 10 escritorio o versiones posteriores (.NET Framework es una versión de escritorio).

 > [!NOTE]
 > Plataformas y aplicaciones no compatibles incluyen ASP.NET 5, 5 de Silverlight y Windows 8.1.
  
 No se admite Editar y continuar al iniciar la depuración con **adjuntar al proceso**. No se admite Editar y continuar para código optimizado o una mezcla de código administrado y nativo. Para obtener más información, consulte [cambios admitidos en el código (C# y Visual Basic](../debugger/supported-code-changes-csharp.md).
  
 En los temas de esta sección se proporciona información adicional sobre cómo utilizar esta característica y los tipos de cambios no permitidos.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Aplicar tareas de edición en modo de interrupción con Editar y continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explica cómo aplicar cambios de código en modo de interrupción.  
  
 [Cambios admitidos en el código (C# y Visual Basic](../debugger/supported-code-changes-csharp.md)   
 Describe los tipos de modificaciones que no pueden realizarse en Editar y continuar de [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Editar y continuar](../debugger/edit-and-continue.md)  
 Ofrece una lista de temas sobre la característica Editar y continuar.