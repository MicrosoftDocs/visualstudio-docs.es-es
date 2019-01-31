---
title: Procedimiento Pasar errores por alto en las tareas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bac63523829c47b17821ff5905687bd76bbc57e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777036"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Procedimiento Pasar por alto errores de las tareas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
A veces, quiere que una compilación tolere errores en determinadas tareas. Si se produce un error en las tareas no críticas, quiere que la compilación continúe porque todavía es posible obtener el resultado esperado. Por ejemplo, si un proyecto utiliza una tarea `SendMail` para enviar un mensaje de correo electrónico después de crear cada componente, tal vez se considere aceptable que la compilación continúe hasta finalizar, aunque los servidores de correo electrónico no estén disponibles ni se puedan enviar los mensajes de estado. O bien, por ejemplo, si los archivos intermedios se suelen eliminar durante la compilación, tal vez se considere aceptable que la compilación continúe hasta finalizar, aunque no se puedan eliminar esos archivos.  
  
## <a name="using-the-continueonerror-attribute"></a>Usar el atributo ContinueOnError  
 El atributo `ContinueOnError` del elemento `Task` controla si una compilación se detiene o continúa cuando se produce un error en la tarea. Este atributo también controla si los errores se tratan como errores o advertencias cuando la compilación continúa.  
  
 El atributo `ContinueOnError` puede contener uno de los siguientes valores:  
  
- **WarnAndContinue** o **true**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento [Target](../msbuild/target-element-msbuild.md) y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como advertencias.  
  
- **ErrorAndContinue**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento `Target` y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como errores.  
  
- **ErrorAndStop** o **false** (valor predeterminado). Cuando se produce un error en una tarea, las tareas restantes en el elemento `Target` y la compilación no se ejecutan, y se considera que se ha producido un error en todo el elemento `Target` y la compilación.  
  
  Las versiones de .NET Framework anteriores a 4.5 solo admiten los valores `true` y `false`.  
  
  El valor predeterminado de `ContinueOnError` es `ErrorAndStop`. Si establece el atributo en `ErrorAndStop`, el comportamiento es explícito para cualquier persona que lea el archivo del proyecto.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Para omitir un error en una tarea  
  
-   Utilice el atributo `ContinueOnError` de la tarea. Por ejemplo:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra que el destino `Build` todavía se ejecuta y la compilación se considera un éxito, incluso si se produce un error en la tarea `Delete`.  
  
```  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también
[MSBuild](msbuild.md)  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)
