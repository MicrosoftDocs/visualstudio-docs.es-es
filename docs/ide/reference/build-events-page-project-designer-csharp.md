---
title: Eventos de compilación (Página, Diseñador de proyectos) (C#)
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4842a5a08de96cd40a45d0765d427cc74cbf5432
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714381"
---
# <a name="build-events-page-project-designer-c"></a>Eventos de compilación (Página, Diseñador de proyectos) (C#)

Use la página **Eventos de compilación** del **Diseñador de proyectos** para especificar las instrucciones de configuración de compilación. También puede especificar las condiciones en las que se ejecutan los eventos posteriores a la compilación. Para obtener más información, vea [Cómo: Especificar eventos de compilación (C#)](../../ide/how-to-specify-build-events-csharp.md) y [Procedimientos: Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Lista de UIElement

**Configuración**

Este control no se puede modificar en esta página. Para obtener una descripción de este control, vea [Página Compilar Diseñador de proyectos (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Plataforma**

Este control no se puede modificar en esta página. Para obtener una descripción de este control, vea [Página Compilar Diseñador de proyectos (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Línea de comandos del evento anterior a la compilación**

Especifica los comandos que se van a ejecutar antes de que empiece la compilación. Para escribir comandos largos, haga clic en **Edición anterior a la compilación** para mostrar el cuadro de diálogo [Línea de comandos del evento anterior a la compilación/Línea de comandos del evento posterior a la compilación](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.

**Línea de comandos del evento posterior a la compilación**

Especifica los comandos que se van a ejecutar después de que finalice la compilación. Para escribir comandos largos, haga clic en **Edición posterior a la compilación** para mostrar el cuadro de diálogo **Línea de comandos del evento anterior a la compilación/Línea de comandos del evento posterior a la compilación**.

> [!NOTE]
> Agregue una instrucción `call` antes de todos los comandos posteriores a la compilación que ejecutan archivos .bat. Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

**Ejecutar el evento posterior a la compilación**

Especifica las condiciones siguientes para que se ejecute el evento posterior a la compilación, como se muestra en la tabla siguiente.

|Opción|Resultado|
|------------|------------|
|**Siempre**|El evento posterior a la compilación se ejecuta independientemente de si la compilación se realiza correctamente.|
|**Si la compilación es correcta**|El evento posterior a la compilación se ejecuta si la compilación se realiza correctamente. Por lo tanto, el evento se ejecutará incluso para un proyecto actualizado, siempre y cuando la compilación se realice correctamente.|
|**Cuando la compilación actualiza la salida del proyecto**|El evento posterior a la compilación solo se ejecuta si el archivo de salida del compilador (.exe o .dll) es diferente del anterior archivo de salida del compilador. Por lo tanto, un evento posterior a la compilación no se ejecuta si un proyecto está actualizado.|

## <a name="in-the-project-file"></a>En el archivo del proyecto

En versiones anteriores de Visual Studio, al cambiar las configuraciones de **PreBuildEvent** o **PostBuildEvent** en el IDE, Visual Studio agregaba una propiedad `PreBuildEvent` o `PostBuildEvent` al archivo del proyecto. Por ejemplo, si la configuración de la línea de comandos **PreBuildEvent** en el IDE es el siguiente:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

entonces la configuración del archivo del proyecto es:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

Para los proyectos de .NET Core, Visual Studio 2019 (y Visual Studio 2017 en las actualizaciones más recientes), agrega un destino de MSBuild denominado `PreBuild` o `PostBuild` para las configuraciones de **PreBuildEvent** y **PostBuildEvent**. Estos destinos usan los atributos **BeforeTargets** y **AfterTargets**, que MSBuild reconoce. Por ejemplo, en el ejemplo anterior, Visual Studio genera ahora el siguiente código:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Para un evento posterior a la compilación, use el nombre `PostBuild` y establezca el atributo `AfterTargets` en `PostBuildEvent`.

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Estos cambios en el archivo del proyecto se realizaron para admitir proyectos de estilo SDK. Si va a migrar manualmente un archivo del proyecto del formato anterior al formato de estilo SDK, debe eliminar las propiedades `PreBuildEvent` y `PostBuildEvent` y reemplazarlas por los destinos `PreBuild` y `PostBuild`, tal como se muestra en el código anterior. Para saber si el proyecto es un proyecto de estilo SDK, vea [Identificación del formato del proyecto](/nuget/resources/check-project-format).

## <a name="see-also"></a>Vea también

- [Cómo: Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Cómo: Especificar eventos de compilación (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)
- [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)