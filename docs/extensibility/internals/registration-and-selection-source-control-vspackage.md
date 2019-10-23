---
title: Registro y selección (VSPackage de control de código fuente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d6ca60c74ae9956f38418ea6048bb0c8050be2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724504"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registro y selección (VSPackage de control de código fuente)
Un VSPackage de control de código fuente debe estar registrado para exponerlo en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Si se registra más de un VSPackage de control de código fuente, el usuario puede seleccionar qué VSPackage cargar en los momentos adecuados. Vea los [VSPackages](../../extensibility/internals/vspackages.md) para obtener más detalles sobre los VSPackages y cómo registrarlos.

## <a name="registering-a-source-control-package"></a>Registrar un paquete de control de código fuente
 El paquete de control de código fuente se registra para que el entorno de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueda encontrarlo y consultar sus características admitidas. Esto es conforme a un esquema de carga retrasada en el que se crea una instancia de un paquete solo cuando sus características o comandos son necesarios o se solicitan explícitamente.

 Los VSPackages colocan información en una clave del registro específica de la versión, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\*X. Y*, donde *X* es el número de versión principal e *y* es el número de versión secundaria. Esta práctica proporciona la capacidad de admitir la instalación en paralelo de varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 La interfaz de usuario (UI) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite la selección entre varios complementos de control de código fuente instalados (a través del paquete del adaptador de control de código fuente), así como VSPackages de control de código fuente. Solo puede haber un complemento de control de código fuente activo o VSPackage a la vez. Sin embargo, tal y como se describe a continuación, el IDE permite cambiar entre complementos de control de código fuente y VSPackages a través de un mecanismo automático de intercambio de paquetes basado en soluciones. Hay algunos requisitos en la parte del VSPackage de control de código fuente para habilitar este mecanismo de selección.

### <a name="registry-entries"></a>Entradas del Registro
 Un paquete de control de código fuente necesita tres GUID privados:

- GUID del paquete: este es el GUID principal del paquete que contiene la implementación del control de código fuente (denominada ID_Package en esta sección).

- GUID de control de código fuente: se trata de un GUID para el VSPackage de control de código fuente utilizado para registrarse con el código auxiliar de control de código fuente de Visual Studio y también se usa como un GUID de contexto de la interfaz de usuario de comandos. El GUID del servicio de control de código fuente se registra bajo el GUID del control de código fuente. En el ejemplo, el GUID del control de código fuente se denomina ID_SccProvider.

- GUID del servicio de control de código fuente: este es el GUID de servicio privado usado por Visual Studio (llamado SID_SccPkgService en esta sección). Además, el paquete de control de código fuente debe definir otros GUID para VSPackages, ventanas de herramientas, etc.

  Las siguientes entradas del registro deben realizarse mediante un VSPackage de control de código fuente:

| Nombre de clave | Entradas |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (valor predeterminado) = rg_sz: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (valor predeterminado) = rg_sz: \<Friendly nombre del paquete ><br /><br /> Servicio = rg_sz: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (valor predeterminado) = rg_sz: # \<Resource ID. para el nombre localizado ><br /><br /> Paquete = rg_sz: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Tenga en cuenta que el nombre de clave, `SourceCodeControl`, ya se usa en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y no está disponible como opción para \<PackageName >). | (valor predeterminado) = rg_sz: {ID_Package} |

## <a name="selecting-a-source-control-package"></a>Seleccionar un paquete de control de código fuente
 Pueden registrarse simultáneamente varios complementos basados en la API de control de código fuente y los paquetes VSPackage de control de código fuente. El proceso de selección de un complemento de control de código fuente o VSPackage debe asegurarse de que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el complemento o el VSPackage en el momento adecuado, y puede diferir la carga de los componentes innecesarios hasta que sean necesarios. Además, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe quitar toda la interfaz de usuario de otros VSPackages inactivos, incluidos los elementos de menú, los cuadros de diálogo y las barras de herramientas, y mostrar la interfaz de usuario del VSPackage activo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga un VSPackage de control de código fuente cuando se realiza una de las operaciones siguientes:

- La solución se abre (cuando la solución está bajo control de código fuente).

   Cuando se abre una solución o un proyecto bajo control de código fuente, el IDE hace que se cargue el VSPackage de control de código fuente que se designó para esa solución.

- Se ejecuta cualquiera de los comandos de menú del VSPackage de control de código fuente.

  Un VSPackage de control de código fuente debe cargar los componentes que necesita solo cuando se van a usar realmente (también conocido como carga retrasada).

### <a name="automatic-solution-based-vspackage-swapping"></a>Intercambio de VSPackage basado en soluciones automática
 Puede intercambiar manualmente los VSPackages de control de código fuente mediante el cuadro de diálogo **Opciones** de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bajo la categoría **control de código fuente** . El intercambio automático de paquetes basado en soluciones significa que un paquete de control de código fuente designado para una solución determinada se establece automáticamente en activo cuando se abre la solución. Cada paquete de control de código fuente debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controla el cambio entre ambos complementos de control de código fuente (implementando la API del complemento de control de código fuente) y los VSPackages de control de código fuente.

 El paquete del adaptador de control de código fuente se usa para cambiar a cualquier complemento basado en la API del complemento de control de código fuente. El proceso de cambiar al paquete del adaptador de control de código fuente intermedio y determinar qué complemento de control de código fuente debe estar establecido en activo o inactivo es transparente para el usuario. El paquete del adaptador siempre está activo cuando cualquier complemento de control de código fuente está activo. Cambiar entre dos complementos de control de código fuente equivale a cargar y descargar la DLL del complemento. Sin embargo, el cambio a un VSPackage de control de código fuente implica interactuar con el IDE para cargar el VSPackage adecuado.

 Se llama a un VSPackage de control de código fuente cuando se abre cualquier solución y la clave del registro para el VSPackage está en el archivo de solución. Cuando se abre la solución, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encuentra el valor del registro y carga el VSPackage de control de código fuente adecuado. Todos los VSPackages del control de código fuente deben tener las entradas del registro descritas anteriormente. Una solución que está bajo control de código fuente se marca como asociada a un VSPackage de control de código fuente concreto. Los VSPackages de control de código fuente deben implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> para habilitar el intercambio de VSPackage basado en soluciones automática.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfaz de usuario de Visual Studio para selección y cambio de paquetes
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona una interfaz de usuario para la selección del VSPackage y el complemento de control de código fuente en el cuadro de diálogo **Opciones** de la categoría **control de código fuente** . Permite al usuario seleccionar el complemento de control de código fuente activo o el VSPackage. Una lista desplegable incluye:

- Todos los paquetes de control de código fuente instalados

- Todos los complementos de control de código fuente instalados

- Una opción "none", que deshabilita el control de código fuente

  Solo está visible la interfaz de usuario de la opción de control de código fuente activa. La selección del VSPackage oculta la interfaz de usuario del VSPackage anterior y muestra la interfaz de usuario para la nueva. El VSPackage activo se selecciona por usuario. Si un usuario tiene varias copias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abiertas simultáneamente, cada una puede usar un VSPackage activo diferente. Si varios usuarios han iniciado sesión en el mismo equipo, cada usuario puede tener instancias independientes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abiertas, cada una con un VSPackage activo diferente. Cuando un usuario cierra varias instancias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], el VSPackage de control de código fuente que estaba activo para la última solución abierta se convierte en el VSPackage de control de código fuente predeterminado, que se establecerá activo al reiniciarse.

  A diferencia de las versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], un reinicio del IDE ya no es la única manera de cambiar los VSPackages de control de código fuente. La selección del VSPackage es automática. El cambio de paquetes requiere privilegios de usuario de Windows (no administrador ni usuario avanzado).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Características](../../extensibility/internals/source-control-vspackage-features.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)