---
title: Registro y la selección (VSPackage de Control de código fuente) | Documentos de Microsoft
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
ms.openlocfilehash: f9bb993f6acaa7cd1cf3980e128e869a643d028c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310910"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registro y selección (VSPackage de control de código fuente)
Un control de código fuente se debe registrar el VSPackage para exponerlo a los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Si se registra más de un VSPackage de control de código fuente, el usuario puede seleccionar qué VSPackage para cargar en los momentos adecuados. Consulte [VSPackages](../../extensibility/internals/vspackages.md) para obtener más detalles sobre los VSPackages y cómo registrarlas.

## <a name="registering-a-source-control-package"></a>Registrar un paquete de Control de código fuente
 Se registra el paquete de control de código fuente para que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno puede encontrar y consulta de sus características admitidas. Se trata de acuerdo con un esquema de carga de retraso en la que se crea una instancia de un paquete solo cuando sus funciones o los comandos son necesarios o que se solicitan explícitamente.

 Los paquetes VSPackage colocan información en una clave del Registro específica de la versión, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, donde *X* es el número de versión principal y *Y* es el número de versión secundaria. Esta práctica proporciona la capacidad para admitir la instalación en paralelo de varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario (UI) admite la selección entre varios código fuente instalado control complementos (mediante el paquete de adaptador de Control de código fuente), así como los paquetes VSPackage de control de código fuente. Puede haber solo un complemento de control de origen activo o VSPackage a la vez. Sin embargo, como se describe a continuación, el IDE permite cambiar entre los complementos de control de código fuente y VSPackages a través de un mecanismo de intercambio de paquetes de basado en la solución automática. Hay algunos requisitos por parte del paquete VSPackage de control de código fuente para habilitar este mecanismo de selección.

### <a name="registry-entries"></a>Entradas del Registro
 Un paquete de control de código fuente necesita tres GUID privados:

- GUID del paquete: Este es el principal GUID del paquete que contiene la implementación del control de código fuente (denominada ID_Package en esta sección).

- GUID de Control de código fuente: Esto es un GUID para el control de código fuente VSPackage que se usa para registrar con código auxiliar Control de origen de Visual Studio y también se usa como un GUID de contexto de la interfaz de usuario de comandos. El GUID del servicio de control de código fuente está registrado con el GUID de control de código fuente. En el ejemplo, el GUID de control de código fuente se denomina ID_SccProvider.

- GUID del servicio de control de código fuente: Éste es el servicio privado GUID que usa Visual Studio (denominado SID_SccPkgService en esta sección). Además, el paquete de control de código fuente debe definir el resto de GUID para paquetes VSPackage, ventanas de herramientas y así sucesivamente.

  Un VSPackage de control de origen se deben realizar las siguientes entradas del registro:

| Nombre de clave | Entradas |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (default) = rg_sz:{ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (valor predeterminado) = rg_sz:\<nombre descriptivo del paquete ><br /><br /> Service = rg_sz:{SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (valor predeterminado) = rg_sz: #\<Id. de recurso para el nombre localizado ><br /><br /> Package = rg_sz:{ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Tenga en cuenta que el nombre de clave, `SourceCodeControl`, ya está usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y no está disponible como una opción para \<PackageName >.) | (default) = rg_sz:{ID_Package} |

## <a name="selecting-a-source-control-package"></a>Seleccionar un paquete de Control de código fuente
 Varios basada en API de complemento de Control de código fuente de complementos y VSPackages se puede registrar al mismo tiempo el control de código fuente. El proceso de selección de un complemento de control de código fuente o el VSPackage debe asegurarse de que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el complemento o VSPackage en el momento adecuado y puede diferir la carga innecesarios componentes hasta que sean necesarios. Además, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe quitar todas las de la interfaz de usuario de otros VSPackages inactivas, incluidos los elementos de menú, cuadros de diálogo y las barras de herramientas y mostrar la interfaz de usuario para el VSPackage activo.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga un paquete VSPackage de control de código fuente cuando se realiza cualquiera de las siguientes operaciones:

- Se abre la solución (cuando la solución está bajo control de código fuente).

   Cuando se abre una solución o proyecto bajo control de código fuente, el IDE hace que el control de código fuente VSPackage que designó para que esa solución para que se va a cargar.

- Cualquiera de los comandos de menú del VSPackage de control de origen se ejecutan.

  Un control de código fuente que VSPackage cargará los componentes que necesita solo cuando realmente se van a ser utilizado (lo que se conoce como la carga diferida).

### <a name="automatic-solution-based-vspackage-swapping"></a>Intercambio automático con paquetes VSPackage basados en la solución
 Los VSPackages de control de código fuente puede intercambiar manualmente a través de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opciones** cuadro de diálogo en el **Control de código fuente** categoría. Intercambio automático de paquetes basado en la solución significa que un paquete de control de código fuente que se ha designado para una solución concreta se establece automáticamente en activo cuando se abre esa solución. Debe implementar cada paquete de control de código fuente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Controla el cambio entre ambos del origen de los complementos de control (implementación de la API de complemento de Control de origen) y VSPackages de control de código fuente.

 El paquete de adaptador de Control de código fuente se utiliza para cambiar a basada en API de complemento de Control de origen de cualquier complemento. El proceso de cambio para el paquete intermedio de adaptador de Control de código fuente y determinar qué complemento de control de código fuente debe establecerse en activo o inactivo es transparente para el usuario. El paquete del adaptador siempre está activo cuando está activa cualquier complemento de control de código fuente. Cambiar entre los dos montos los complementos de control de origen a simplemente carga y descarga la DLL del complemento. Cambiar a un VSPackage de control de código fuente, sin embargo, implica interactuar con el IDE para cargar el VSPackage adecuado.

 Un control de código fuente VSPackage se llama cuando se abra cualquier solución y la clave del registro para el VSPackage está en el archivo de solución. Cuando se abre la solución, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] busca el valor del registro y carga el VSPackage de control de origen adecuado. Todos los VSPackages de control de código fuente debe tener las entradas del registro que se ha descrito anteriormente. Una solución que está bajo control de código fuente está marcada como que está asociada a un VSPackage de control de origen determinado. Los paquetes VSPackage deben implementar el control de código fuente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> para permitir el VSPackage basado en la solución automática intercambio.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfaz de usuario para la selección de paquete y el cambio de Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proporciona una interfaz de usuario de VSPackage de control de código fuente y la selección de complemento en el **opciones** cuadro de diálogo en el **Control de código fuente** categoría. Permite al usuario seleccionar el complemento de control de origen activo o el VSPackage. Incluye una lista desplegable:

- Todos los paquetes de control de código fuente instalado

- Instalado todos los complementos de control de código fuente

- Una opción "Ninguno", que deshabilita el control de código fuente

  Solo la interfaz de usuario para la opción de control de origen activo está visible. La selección de VSPackage oculta la interfaz de usuario para el VSPackage anterior y muestra la interfaz de usuario para el nuevo. El VSPackage activo está activado en por usuario. Si un usuario tiene varias copias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abiertos al mismo tiempo, cada uno de ellos puede utilizar potencialmente un VSPackage activo diferente. Si varios usuarios se registran el mismo equipo, cada usuario puede tener instancias independientes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abrir, cada uno con un VSPackage activo diferente. Cuando varias instancias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] están cerradas por un usuario, el control de código fuente VSPackage que estaba activo para la última solución abierta se convierte en el control de código fuente predeterminada VSPackage debe establecerse activo en el reinicio.

  A diferencia de las versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], un reinicio IDE ya no es la única manera de cambiar los VSPackages de control de código fuente. Selección de VSPackage es automática. Conmutación de paquetes requiere privilegios de usuario de Windows (no administrador o usuario avanzado).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Características](../../extensibility/internals/source-control-vspackage-features.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)