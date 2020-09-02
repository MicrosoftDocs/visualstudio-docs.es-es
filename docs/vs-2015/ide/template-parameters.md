---
title: Parámetros de plantilla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d7bb7e0f3dfee3dd1bf3e9b42afd5837a29f6ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646808"
---
# <a name="template-parameters"></a>Parámetros de plantilla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si se usan parámetros en las plantillas, se pueden reemplazar los valores de las partes principales de la plantilla, como nombres de clase y espacios de nombres, cuando se crean instancias de la plantilla. Estos parámetros se reemplazan por el asistente de la plantilla que se ejecuta en segundo plano cuando el usuario hace clic en **Aceptar** en los cuadros de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.

## <a name="declaring-and-enabling-template-parameters"></a>Declarar y habilitar parámetros de plantilla
 Los parámetros de plantilla se declaran en el formato $*parámetro*$. Por ejemplo:

- $safeprojectname$

- $guid1$

- $guid5$

#### <a name="to-enable-parameter-substitution-in-templates"></a>Para habilitar la substitución de parámetros en las plantillas

1. En el archivo .vstemplate de la plantilla, busque el elemento `ProjectItem` correspondiente al elemento para el que desea habilitar el reemplazo de parámetros.

2. Establezca el atributo `ReplaceParameters` del elemento `ProjectItem` en `true`:

3. En el archivo de código del elemento de proyecto, incluya los parámetros donde proceda. Por ejemplo, el parámetro siguiente especifica que se debe utilizar el nombre del proyecto seguro para el espacio de nombres en un archivo:

    ```
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Parámetros de plantilla reservados
 La tabla siguiente muestra los parámetros de plantilla reservados que cualquier plantilla puede utilizar.

> [!NOTE]
> Los parámetros de plantilla distinguen entre mayúsculas y minúsculas.

|Parámetro|Descripción|
|---------------|-----------------|
|`clrversion`|Versión actual del Common Language Runtime (CLR).|
|`GUID [1-10]`|GUID utilizado para reemplazar el GUID del proyecto en un archivo de proyecto. Puede especificar hasta 10 GUID únicos (por ejemplo, `guid1)`.|
|`itemname`|Nombre proporcionado por el usuario en el cuadro de diálogo **Agregar nuevo elemento**.|
|`machinename`|Nombre del equipo actual (por ejemplo, Equipo01).|
|`projectname`|Nombre proporcionado por el usuario en el cuadro de diálogo **Nuevo proyecto**.|
|`registeredorganization`|Valor de la clave del Registro de HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|`rootnamespace`|Espacio de nombres raíz del proyecto actual. Este parámetro solo se aplica a las plantillas de elementos.|
|`safeitemname`|Nombre proporcionado por el usuario en el cuadro de diálogo **Agregar nuevo elemento**, tras quitar todos los caracteres no seguros y los espacios.|
|`safeprojectname`|Nombre proporcionado por el usuario en el cuadro de diálogo **Nuevo proyecto**, tras quitar todos los caracteres no seguros y los espacios.|
|`time`|Hora actual en el formato DD/MM/AAAA 00:00:00.|
|`SpecificSolutionName`|Nombre de la solución. Cuando se activa "Crear directorio para la solución", `SpecificSolutionName` tiene el nombre de la solución. Cuando no se activa "Crear directorio para la solución", `SpecificSolutionName` está en blanco.|
|`userdomain`|Dominio del usuario actual.|
|`username`|Nombre de usuario actual.|
|`webnamespace`|Nombre del sitio web actual. Este parámetro se utiliza en la plantilla de formulario Web Forms para garantizar que los nombres de clase sean únicos. Si el sitio web está en el directorio raíz del servidor web, este parámetro de plantilla se resuelve como el directorio raíz del servidor web.|
|`year`|Año actual en formato AAAA.|

## <a name="custom-template-parameters"></a>Parámetros de plantilla personalizados
 Puede especificar sus propios parámetros y valores de plantilla, además de los parámetros de plantilla reservados predeterminados que se usan durante el reemplazo de parámetros. Para obtener más información, vea [CustomParameters Element (Visual Studio Templates)](../extensibility/customparameters-element-visual-studio-templates.md) (Elemento CustomParameters (plantillas de Visual Studio)).

## <a name="example-replacing-files-names"></a>Ejemplo: Reemplazar nombres de archivos
 Puede especificar nombres de archivo variables para los elementos de proyecto utilizando un parámetro con el atributo `TargetFileName`. Por ejemplo, podría especificar que el archivo .exe use el nombre del proyecto, especificado por `$projectname$`, como su nombre de archivo.

```
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-project-name-for-the-namespace-name"></a>Ejemplo: Utilizar el nombre de proyecto para el nombre del espacio de nombres
 Para utilizar el nombre del proyecto para el espacio de nombres en un archivo de clase de Visual C#, Class1.cs, utilice la sintaxis siguiente:

```
#region Using directives

using System;
using System.Collections.Generic;
using System.Text;

#endregion

namespace $safeprojectname$
{
    public class Class1
        {
            public Class1()
                {

                }
         }
}
```

 En el archivo .vstemplate para la plantilla de proyecto, incluya el XML siguiente al hacer referencia al archivo Class1.cs:

```
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Consulte también
 [Personalización de plantillas](../ide/customizing-project-and-item-templates.md)
