---
title: Editar y continuar (Visual Basic) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61ce8f61092bdcc612ea535debfcface976ebff8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265134"
---
# <a name="edit-and-continue-visual-basic"></a>Editar y continuar (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editar y continuar es una característica de depuración de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] que le permite realizar cambios en el código mientras se ejecuta en modo de interrupción. Una vez que se aplican los cambios de código, se puede reanudar su ejecución con las nuevas modificaciones en contexto y observar el efecto.  
  
 Es posible utilizar la característica Editar y continuar cada vez que se entra en el modo de interrupción. En modo de interrupción, el puntero de instrucciones (una punta de flecha amarilla en la ventana de código fuente) señala la línea que se ejecutará a continuación y se ubicará en una instrucción ejecutable dentro de un cuerpo de método o propiedad. Se puede realizar casi cualquier tipo de cambio en las instrucciones ejecutables mientras se está en modo de interrupción; dicho cambio se incorporará al proyecto subyacente. Sin embargo, mientras se está en modo de interrupción no se permite, por lo general, realizar cambios en instrucciones de declaración, como métodos, campos públicos o declaraciones de clase.  
  
 Cuando se realiza una modificación que no está autorizada, el cambio se marca con un subrayado ondulado de color púrpura y aparece una tarea en la Lista de tareas. Si desea seguir utilizando Editar y continuar, debe deshacer el cambio no autorizado. Es posible que algunas modificaciones no autorizadas puedan realizarse fuera de Editar y continuar. Si desea retener los resultados de dicha modificación no autorizada, deberá detener la depuración y reiniciar la aplicación.  
  
 Editar y continuar se admite para proyectos 64 bits destinados a .NET Framework 4.5.1.  
  
 No se admite Editar y continuar al iniciar la depuración mediante **asociar al proceso**. Editar y continuar no se admite para el código optimizado, el código mixto (administrado y nativo) o los proyectos de Compact Framework (Smart Device).  
  
 En los temas de esta sección se proporciona información adicional sobre cómo utilizar esta característica y los tipos de cambios no permitidos.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Aplicar tareas de edición en modo de interrupción con Editar y continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explica cómo aplicar cambios de código en modo de interrupción.  
  
 [Ediciones no compatibles en Editar y continuar de Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Describe los tipos de modificaciones que no pueden realizarse en Editar y continuar de [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Editar y continuar](../debugger/edit-and-continue.md)  
 Ofrece una lista de temas sobre la característica Editar y continuar.



