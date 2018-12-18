---
title: Parámetros de plantilla de elemento y de proyecto de Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4c76eaf68f63b4f3b8a5713d0b206b395ee7c9f1
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178639"
---
# <a name="template-parameters"></a>Parámetros de plantilla

Es posible sustituir valores de la plantilla cuando se crea una instancia de ella. Para configurar esta funcionalidad, use *parámetros de plantilla*. Los parámetros de plantilla pueden usarse para sustituir valores como nombres de clase y espacios de nombres de la plantilla. El asistente para plantillas que se ejecuta en segundo plano cuando un usuario agrega un nuevo elemento o proyecto reemplaza estos parámetros.

## <a name="declaring-and-enabling-template-parameters"></a>Declarar y habilitar parámetros de plantilla

Los parámetros de plantilla se declaran en el formato $*parámetro*$. Por ejemplo:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>Para habilitar la substitución de parámetros en las plantillas

1. En el archivo *.vstemplate* de la plantilla, busque el elemento `ProjectItem` correspondiente al elemento para el que quiere habilitar el reemplazo de parámetros.

1. Establezca el atributo `ReplaceParameters` del elemento `ProjectItem` en `true`:

1. En el archivo de código del elemento de proyecto, incluya los parámetros donde proceda. Por ejemplo, el parámetro siguiente especifica que se usa el nombre de proyecto seguro para el espacio de nombres de un archivo:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Parámetros de plantilla reservados

La tabla siguiente muestra los parámetros de plantilla reservados que cualquier plantilla puede utilizar.

|Parámetro|Descripción|
|---------------|-----------------|
|clrversion|Versión actual del Common Language Runtime (CLR).|
|guid[1-10]|GUID utilizado para reemplazar el GUID del proyecto en un archivo de proyecto. Puede especificar hasta 10 GUID únicos (por ejemplo, `guid1`).|
|itemname|Nombre proporcionado por el usuario en el cuadro de diálogo **Agregar nuevo elemento**.|
|machinename|Nombre del equipo actual (por ejemplo, Equipo01).|
|projectname|Nombre proporcionado por el usuario en el cuadro de diálogo **Nuevo proyecto**.|
|registeredorganization|Valor de la clave del Registro de HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Espacio de nombres raíz del proyecto actual. Este parámetro solo se aplica a las plantillas de elementos.|
|safeitemname|Nombre proporcionado por el usuario en el cuadro de diálogo **Agregar nuevo elemento**, tras quitar todos los caracteres no seguros y los espacios.|
|safeprojectname|Nombre proporcionado por el usuario en el cuadro de diálogo **Nuevo proyecto**, tras quitar todos los caracteres no seguros y los espacios.|
|hora|Hora actual en el formato DD/MM/AAAA 00:00:00.|
|SpecificSolutionName|Nombre de la solución. Cuando se activa "Crear directorio para la solución", `SpecificSolutionName` tiene el nombre de la solución. Cuando no se activa "Crear directorio para la solución", `SpecificSolutionName` está en blanco.|
|userdomain|Dominio del usuario actual.|
|username|Nombre de usuario actual.|
|webnamespace|Nombre del sitio web actual. Este parámetro se usa en la plantilla de formulario web para garantizar que los nombres de clase sean únicos. Si el sitio web está en el directorio raíz del servidor web, este parámetro de plantilla se resuelve como el directorio raíz del servidor web.|
|año|Año actual en formato AAAA.|

> [!NOTE]
> Los parámetros de plantilla distinguen entre mayúsculas y minúsculas.

## <a name="custom-template-parameters"></a>Parámetros de plantilla personalizados

Puede especificar sus propios parámetros y valores de plantilla, además de los parámetros de plantilla reservados predeterminados que se usan durante el reemplazo de parámetros. Para obtener más información, consulte [CustomParameters element (Visual Studio templates)](../extensibility/customparameters-element-visual-studio-templates.md) (Elemento CustomParameters (plantillas de Visual Studio)).

## <a name="example-use-the-project-name-for-a-file-name"></a>Ejemplo: Uso del nombre del proyecto para un nombre de archivo

Puede especificar nombres de archivo variables para los elementos de proyecto usando un parámetro en el atributo `TargetFileName`.

En el ejemplo siguiente se especifica que el nombre de un archivo ejecutable usa el nombre del proyecto, especificado por `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Ejemplo: Uso del nombre de proyecto seguro para el nombre del espacio de nombres

Para usar el nombre del proyecto seguro para el espacio de nombres en un archivo de clase de C#, use la sintaxis siguiente:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

En el archivo *.vstemplate* de la plantilla de proyecto, incluya el atributo `ReplaceParameters="true"` al hacer referencia al archivo:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Vea también

- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md)
- [Referencia de esquema de plantillas](../extensibility/visual-studio-template-schema-reference.md)
