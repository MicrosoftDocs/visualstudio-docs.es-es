---
title: Solución (. Sln) archivo
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705327"
---
# <a name="solution-sln-file"></a>Solución (.sln) archivo

Una solución es una estructura para organizar proyectos en Visual Studio. La solución mantiene la información de estado de los proyectos en dos archivos:

- Archivo .sln (basado en texto, compartido)

- Archivo .suo (opciones de solución binarias específicas del usuario)

Para obtener más información acerca de los archivos .suo, vea Opciones de usuario de la [solución (. Suo) Archivo](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Si el VSPackage se carga como resultado de que se hace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> referencia en el archivo .sln, el entorno llama para leer en el archivo .sln.

El archivo .sln contiene información basada en texto que el entorno utiliza para buscar y cargar los parámetros nombre-valor para los datos persistentes y el proyecto VSPackages al que hace referencia. Cuando un usuario abre una solución, `Project`el `postSolution` entorno recorre el `preSolution`archivo , e información del archivo .sln para cargar la solución, los proyectos dentro de la solución y cualquier información persistente asociada a la solución.

El archivo de cada proyecto contiene información adicional leída por el entorno para rellenar la jerarquía con los elementos de ese proyecto. El proyecto controla la persistencia de los datos de jerarquía. Los datos no se almacenan normalmente en el archivo .sln, aunque puede escribir intencionalmente información del proyecto en el archivo .sln si decide hacerlo. Para obtener más información acerca de la persistencia, vea [Persistencia](../../extensibility/internals/project-persistence.md) del proyecto y [Abrir y guardar elementos](../../extensibility/internals/opening-and-saving-project-items.md)de proyecto .

## <a name="file-header"></a>Encabezado del archivo

El encabezado de un archivo .sln tiene este aspecto:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definiciones

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Encabezado estándar que define la versión del formato de archivo.

`# Visual Studio 15`\
La versión principal de Visual Studio que (más recientemente) guardó este archivo de solución. Esta información controla el número de versión en el icono de la solución.

`VisualStudioVersion = 15.0.26730.15`\
La versión completa de Visual Studio que (más recientemente) guardó el archivo de solución. Si el archivo de solución se guarda mediante una versión más reciente de Visual Studio que tiene la misma versión principal, este valor no se actualiza para disminuir la renovación en los archivos de solución.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La versión mínima (más antigua) de Visual Studio que puede abrir este archivo de solución.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definiciones

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Encabezado estándar que define la versión del formato de archivo.

`# Visual Studio Version 16`\
La versión principal de Visual Studio que (más recientemente) guardó este archivo de solución. Esta información controla el número de versión en el icono de la solución.

`VisualStudioVersion = 16.0.28701.123`\
La versión completa de Visual Studio que (más recientemente) guardó el archivo de solución. Si el archivo de solución se guarda mediante una versión más reciente de Visual Studio que tiene la misma versión principal, este valor no se actualiza para disminuir la renovación en el archivo.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La versión mínima (más antigua) de Visual Studio que puede abrir este archivo de solución.

::: moniker-end

## <a name="file-body"></a>Cuerpo del archivo

El cuerpo de un archivo .sln `GlobalSection`consta de varias secciones etiquetadas, como esta:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Para cargar una solución, el entorno realiza la siguiente secuencia de tareas:

1. El entorno lee la sección Global del archivo .sln y procesa todas las secciones marcadas `preSolution`. En este archivo de ejemplo, hay una instrucción de este tipo:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Cuando el entorno `GlobalSection('name')` lee la etiqueta, asigna el nombre a un VSPackage mediante el registro. El nombre de la clave debe\\ existir en el\>registro en [HKLM<raíz del Registro de ID de aplicación . El valor predeterminado de las claves es el GUID de paquete (REG_SZ) del VSPackage que escribió las entradas.

2. El entorno carga el `QueryInterface` VSPackage, llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> al VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> para la interfaz y llama al método con los datos de la sección para que el VSPackage pueda almacenar los datos. El entorno repite este `preSolution` proceso para cada sección.

3. El entorno recorre en iteración los bloques de persistencia del proyecto. En este caso, hay un proyecto.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Esta instrucción contiene el GUID de proyecto único y el GUID de tipo de proyecto. El entorno usa esta información para buscar el archivo de proyecto o los archivos que pertenecen a la solución y el VSPackage necesario para cada proyecto. El GUID del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> proyecto se pasa a cargar el VSPackage específico relacionado con el proyecto, a continuación, el proyecto se carga mediante el VSPackage. En este caso, el VSPackage que se carga para este proyecto es Visual Basic.

   Cada proyecto puede conservar un identificador de instancia de proyecto único para que se pueda tener acceso a él según sea necesario para otros proyectos de la solución. Idealmente, si la solución y los proyectos están bajo control de código fuente, la ruta de acceso al proyecto debe ser relativa a la ruta de acceso a la solución. Cuando se carga la solución por primera vez, los archivos de proyecto no pueden estar en el equipo del usuario. Al tener el archivo de proyecto almacenado en el servidor en relación con el archivo de solución, es relativamente sencillo encontrar el archivo de proyecto y copiarlo en el equipo del usuario. A continuación, copia y carga el resto de los archivos necesarios para el proyecto.

4. En función de la información contenida en la sección de proyecto del archivo .sln, el entorno carga cada archivo de proyecto. A continuación, el propio proyecto es responsable de rellenar la jerarquía del proyecto y cargar los proyectos anidados.

5. Después de procesar todas las secciones del archivo .sln, la solución se muestra en el Explorador de soluciones y está lista para su modificación por parte del usuario.

Si cualquier VSPackage que implementa un proyecto en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> la solución no se puede cargar, se llama al método y todos los demás proyectos de la solución tienen la oportunidad de omitir los cambios que podría haber realizado durante la carga. Si se producen errores de análisis, se conserva tanta información como sea posible con los archivos de solución y el entorno muestra un cuadro de diálogo que advierte al usuario de que la solución está dañada.

Cuando se guarda o se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> cierra la solución, se llama al método y se pasa a la jerarquía para ver si se han realizado cambios en la solución que se deben escribir en el archivo .sln. Un valor nulo, `QuerySaveSolutionProps` pasado <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>a , indica que la información se conserva para la solución. Si el valor no es null, la información persistente es para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> un proyecto específico, determinado por el puntero a la interfaz.

Si hay información que se <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> va a guardar, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> se llama a la interfaz con un puntero al método. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> continuación, el entorno llama al método para `IPropertyBag` recuperar los pares nombre-valor de la interfaz y escribir la información en el archivo .sln.

`SaveSolutionProps`y `WriteSolutionProps` el entorno llama recursivamente a los objetos `IPropertyBag` para recuperar la información que se guardará de la interfaz hasta que se hayan introducido todos los cambios en el archivo .sln. De este modo, puede asegurarse de que la información se conservará con la solución y estará disponible la próxima vez que se abra la solución.

Cada VSPackage cargado se enumera para ver si tiene algo que guardar en el archivo .sln. Es sólo en el momento de la carga que se consultan las claves del registro. El entorno conoce todos los paquetes cargados porque están en memoria en el momento en que se guarda la solución.

Solo el archivo .sln contiene `preSolution` `postSolution` entradas en las secciones y. No hay secciones similares en el archivo .suo, ya que la solución necesita esta información para cargar correctamente. El archivo .suo contiene opciones específicas del usuario, como notas privadas, que no están diseñadas para compartirse ni colocarse bajo control de código fuente.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Archivo de opciones de usuario de la solución (.Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Soluciones](../../extensibility/internals/solutions-overview.md)
