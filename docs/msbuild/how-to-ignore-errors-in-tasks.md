---
title: Procedimiento Pasar errores por alto en las tareas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.openlocfilehash: f271c2d6dae3857818505829cf2da8a109613e9a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852695"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Procedimiento Pasar errores por alto en las tareas
A veces, quiere que una compilación tolere errores en determinadas tareas. Si se produce un error en las tareas no críticas, quiere que la compilación continúe porque todavía es posible obtener el resultado esperado. Por ejemplo, si un proyecto utiliza una tarea `SendMail` para enviar un mensaje de correo electrónico después de crear cada componente, tal vez se considere aceptable que la compilación continúe hasta finalizar, aunque los servidores de correo electrónico no estén disponibles ni se puedan enviar los mensajes de estado. O bien, por ejemplo, si los archivos intermedios se suelen eliminar durante la compilación, tal vez se considere aceptable que la compilación continúe hasta finalizar, aunque no se puedan eliminar esos archivos.  
  
## <a name="use-the-continueonerror-attribute"></a>Usar el atributo ContinueOnError  
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
  
```xml  
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
[MSBuild](../msbuild/msbuild.md)  
[Referencia de tareas](../msbuild/msbuild-task-reference.md)   
[Tareas](../msbuild/msbuild-tasks.md)