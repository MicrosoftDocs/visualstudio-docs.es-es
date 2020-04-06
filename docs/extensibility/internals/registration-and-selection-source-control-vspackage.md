---
title: Registro y selección (VSPackage de control de código fuente) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705717"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registro y selección (VSPackage de control de código fuente)
Un control de código fuente VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]debe estar registrado para exponerlo a la . Si se registra más de un control de código fuente VSPackage, el usuario puede seleccionar qué VSPackage para cargar en los momentos adecuados. Vea [VSPackages](../../extensibility/internals/vspackages.md) para obtener más detalles sobre VSPackages y cómo registrarlos.

## <a name="registering-a-source-control-package"></a>Registro de un paquete de control de código fuente
 El paquete de control de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] código fuente se registra para que el entorno pueda encontrarlo y consultar sus características admitidas. Esto es de acuerdo con un esquema de carga de retraso en el que se crea una instancia de un paquete solo cuando sus características o comandos son necesarios o se solicitan explícitamente.

 LOS VSPackages colocan la información en una clave del Registro\\específica de la versión, HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft VisualStudio*X.Y*, donde *X* es el número de versión principal y *Y* es el número de versión secundaria. Esta práctica proporciona la capacidad de admitir la instalación [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]en paralelo de varias versiones de .

 La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario (UI) admite la selección entre varios complementos de control de código fuente instalados (a través del paquete de adaptador de control de código fuente) así como VSPackages de control de código fuente. Solo puede haber un complemento de control de código fuente activo o VSPackage a la vez. Sin embargo, como se describe a continuación, el IDE permite cambiar entre complementos de control de código fuente y VSPackages a través de un mecanismo de intercambio de paquetes basado en solución automática. Hay algunos requisitos por parte del control de código fuente VSPackage para habilitar este mecanismo de selección.

### <a name="registry-entries"></a>Entradas del Registro
 Un paquete de control de código fuente necesita tres GUID privados:

- GUID del paquete: este es el GUID principal del paquete que contiene la implementación del control de código fuente (denominada ID_Package en esta sección).

- GUID de Control de código fuente: este es un GUID para el control de código fuente VSPackage utilizado para registrarse con el código auxiliar de Control de código fuente de Visual Studio y también se usa como un GUID de contexto de interfaz de usuario de comando. El GUID del servicio de control de código fuente se registra en el GUID del control de código fuente. En el ejemplo, el GUID del control de código fuente se denomina ID_SccProvider.

- GUID del servicio de control de código fuente: este es el GUID de servicio privado utilizado por Visual Studio (denominado SID_SccPkgService en esta sección). Además de esto, el paquete de control de código fuente debe definir otros GUID para VSPackages, ventanas de herramientas, etc.

  Las siguientes entradas del Registro deben realizarse mediante un control de código fuente VSPackage:

| Nombre de clave | Entradas |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (predeterminado) - rg_sz:-ID_SccProvider- |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (predeterminado) -\<rg_sz: nombre descriptivo del paquete><br /><br /> Servicio: rg_sz:SID_SccPkgService |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (predeterminado): rg_sz:\<id de recurso para el nombre localizado><br /><br /> Paquete srg_sz:-ID_Package |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Tenga en cuenta `SourceCodeControl`que el nombre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de clave, , \<ya está utilizado por y no está disponible como una opción para PackageName>.) | (predeterminado) - rg_sz: ID_Package |

## <a name="selecting-a-source-control-package"></a>Selección de un paquete de control de código fuente
 Varios complementos basados en API de complemento de Control de código fuente y VSPackages de control de código fuente se pueden registrar simultáneamente. El proceso de selección de un complemento de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] control de código fuente o VSPackage debe asegurarse de que carga el complemento o VSPackage en el momento adecuado y puede aplazar la carga de componentes innecesarios hasta que sean necesarios. Además, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe quitar toda la interfaz de usuario de otros VSPackages inactivos, incluidos los elementos de menú, cuadros de diálogo y barras de herramientas y mostrar la interfaz de usuario para el VSPackage activo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]carga un control de código fuente VSPackage cuando se realiza cualquiera de las siguientes operaciones:

- La solución se abre (cuando la solución está bajo control de código fuente).

   Cuando se abre una solución o proyecto bajo control de código fuente, el IDE hace que se cargue el control de código fuente VSPackage que se designó para esa solución.

- Se ejecuta cualquiera de los comandos de menú del control de código fuente VSPackage.

  Un control de código fuente VSPackage debe cargar los componentes que necesita solo cuando realmente se van a usar (también conocido como carga retrasada).

### <a name="automatic-solution-based-vspackage-swapping"></a>Intercambio automático de VSPackage basado en soluciones
 Puede intercambiar manualmente el control de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] código fuente VSPackages a través del cuadro de diálogo **Opciones** en la categoría **Control de código fuente.** El intercambio automático de paquetes basado en soluciones significa que un paquete de control de código fuente que se ha designado para una solución determinada se establece automáticamente en activo cuando se abre esa solución. Cada paquete de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> control <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>de código fuente debe implementar y . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]controla el conmutador entre ambos complementos de control de código fuente (implementación de la API de complemento de Control de código fuente) y VSPackages de control de código fuente.

 El paquete de adaptador de Control de código fuente se usa para cambiar a cualquier complemento basado en API de complemento de Control de código fuente. El proceso de cambiar al paquete de adaptador de control de código fuente intermedio y determinar qué complemento de control de código fuente debe establecerse en activo o inactivo es transparente para el usuario. El paquete de adaptador siempre está activo cuando cualquier complemento de control de código fuente está activo. Cambiar entre dos complementos de control de código fuente equivale a simplemente cargar y descargar el archivo DLL del complemento. Cambiar a un control de código fuente VSPackage, sin embargo, implica interactuar con el IDE para cargar el VSPackage adecuado.

 Se llama a un control de código fuente VSPackage cuando se abre cualquier solución y la clave del Registro para el VSPackage está en el archivo de solución. Cuando se abre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la solución, busca el valor del Registro y carga el control de código fuente adecuado VSPackage. Todos los VSPackages de control de código fuente deben tener las entradas del Registro descritas anteriormente. Una solución que está bajo control de código fuente se marca como asociada a un control de código fuente determinado VSPackage. VSPackages de control <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> de código fuente debe implementar el para habilitar el intercambio de VSPackage basado en solución automática.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfaz de usuario de Visual Studio para la selección y conmutación de paquetes
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proporciona una interfaz de usuario para el control de código fuente VSPackage y selección de complementos en el **opciones** cuadro de diálogo en el **Control de código fuente** categoría. Permite al usuario seleccionar el complemento de control de código fuente activo o VSPackage. Una lista desplegable incluye:

- Todos los paquetes de control de código fuente instalados

- Todos los complementos de control de código fuente instalados

- Una opción "ninguno", que deshabilita el control de código fuente

  Solo está visible la interfaz de usuario de la opción de control de código fuente activo. La selección de VSPackage oculta la interfaz de usuario para el VSPackage anterior y muestra la interfaz de usuario para el nuevo. El VSPackage activo se selecciona por usuario. Si un usuario tiene [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] varias copias de abierto simultáneamente, cada uno puede usar un VSPackage activo diferente. Si varios usuarios han iniciado sesión en el mismo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] equipo, cada usuario puede tener instancias independientes de abierto, cada uno con un VSPackage activo diferente. Cuando varias instancias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] son cerradas por un usuario, el control de código fuente VSPackage que estaba activo para la última solución abierta se convierte en el control de código fuente predeterminado VSPackage, que se establecerá activo en el reinicio.

  A diferencia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de las versiones anteriores de , un reinicio IDE ya no es la única manera de cambiar VSPackages de control de código fuente. La selección de VSPackage es automática. Cambiar paquetes requiere privilegios de usuario de Windows (no administrador o usuario avanzado).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Características](../../extensibility/internals/source-control-vspackage-features.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)
