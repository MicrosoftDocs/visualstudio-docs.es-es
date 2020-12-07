---
title: Parámetros de plantilla de elemento y de proyecto
description: Aprenda a usar parámetros de plantilla para sustituir valores de la plantilla cuando se crea una instancia de ella.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 8e575011f76370083b5a0f461fbb62bbbc839ea3
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479209"
---
# <a name="template-parameters"></a>Parámetros de plantilla

Es posible sustituir valores de la plantilla cuando se crea una instancia de ella. Para configurar esta funcionalidad, use *parámetros de plantilla*. Los parámetros de plantilla pueden usarse para sustituir valores como nombres de clase y espacios de nombres de la plantilla. El asistente para plantillas que se ejecuta en segundo plano cuando un usuario agrega un nuevo elemento o proyecto reemplaza estos parámetros.

## <a name="declare-and-enable-template-parameters"></a>Declaración y habilitación de parámetros de plantilla

Los parámetros de plantilla se declaran en el formato $*parámetro*$. Por ejemplo:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Habilitación de la sustitución de parámetros en las plantillas

1. En el archivo *.vstemplate* de la plantilla, busque el elemento `ProjectItem` correspondiente al elemento para el que quiere habilitar el reemplazo de parámetros.

1. Establezca el atributo `ReplaceParameters` del elemento `ProjectItem` en `true`:

1. En el archivo de código del elemento de proyecto, incluya los parámetros donde proceda. Por ejemplo, el parámetro siguiente especifica que se usa el nombre de proyecto seguro para el espacio de nombres de un archivo:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Parámetros de plantilla reservados

En la tabla siguiente se muestran los parámetros de plantilla reservados que se pueden usar en cualquier plantilla:

|Parámetro|Descripción|
|---------------|-----------------|
|clrversion|Versión actual del Common Language Runtime (CLR).|
|ext_*|Agrega el prefijo `ext_` a cualquier parámetro para hacer referencia a las variables de la plantilla principal. Por ejemplo, `ext_safeprojectname`.|
|guid[1-10]|GUID utilizado para reemplazar el GUID del proyecto en un archivo de proyecto. Puede especificar hasta 10 GUID únicos (por ejemplo, `guid1`).|
|itemname|El nombre del archivo en el que se usa el parámetro.|
|machinename|Nombre del equipo actual (por ejemplo, Equipo01).|
|projectname|Nombre especificado por el usuario al crear el proyecto.|
|registeredorganization|Valor de la clave del Registro de HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Espacio de nombres raíz del proyecto actual. Este parámetro solo se aplica a las plantillas de elementos.|
|safeitemname|Igual que `itemname`, pero con todos los caracteres no seguros y los espacios reemplazados por caracteres de subrayado.|
|safeitemrootname|Igual a `safeitemname`.|
|safeprojectname|Nombre especificado por el usuario al crear el proyecto, tras quitar todos los caracteres no seguros y los espacios.|
|time|Hora actual en el formato DD/MM/AAAA 00:00:00.|
|specifiedsolutionname|Nombre de la solución. Cuando se activa "Crear directorio para la solución", `specifiedsolutionname` tiene el nombre de la solución. Cuando no se activa "Crear directorio para la solución", `specifiedsolutionname` está en blanco.|
|userdomain|Dominio del usuario actual.|
|username|Nombre de usuario actual.|
|webnamespace|Nombre del sitio web actual. Este parámetro se usa en la plantilla de formulario web para garantizar que los nombres de clase sean únicos. Si el sitio web está en el directorio raíz del servidor web, este parámetro de plantilla se resuelve como el directorio raíz del servidor web.|
|year|Año actual en formato AAAA.|

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

## <a name="see-also"></a>Consulte también

- [Cómo: Sustituir parámetros en una plantilla](how-to-substitute-parameters-in-a-template.md)
- [Personalizar plantillas](../ide/customizing-project-and-item-templates.md)
- [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md)
- [Referencia de esquema de plantillas](../extensibility/visual-studio-template-schema-reference.md)
