---
title: "Registro y la selecci&#243;n (VSPackage de Control de c&#243;digo fuente) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "registro de paquetes de control de código fuente"
  - "paquetes de control de código fuente, registro"
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# Registro y la selecci&#243;n (VSPackage de Control de c&#243;digo fuente)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un control de código fuente se debe registrar VSPackage para exponerlo a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Si se registra más de un control de código fuente VSPackage, el usuario puede seleccionar qué VSPackage para cargar en los momentos adecuados. Vea [VSPackages](../../extensibility/internals/vspackages.md) para obtener más información sobre VSPackages y cómo registrarlos.  
  
## <a name="registering-a-source-control-package"></a>Registrar un paquete de Control de código fuente  
 El paquete de control de origen se registra para que la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno puede encontrar y consulta de sus características admitidas. Esto es conforme con un esquema de carga retrasada en la que se crea una instancia de un paquete solo cuando sus funciones o los comandos son necesarios o que se solicitan explícitamente.  
  
 VSPackages colocar la información en una clave del Registro específica de la versión, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, donde *X* es el número de versión principal y *Y* es el número de versión secundaria. Esta práctica proporciona la capacidad para admitir la instalación en paralelo de varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario (UI) admite la selección entre varios código fuente instalado control complementos (mediante el paquete de adaptador de Control de origen), así como el control de código fuente VSPackages. Puede haber solo un complemento de control de origen activo o VSPackage a la vez. Sin embargo, tal y como se describe a continuación, el IDE permite cambiar entre los complementos de control de código fuente y VSPackages a través de un mecanismo de intercambio de paquetes de basado en la solución automática. Existen algunos requisitos por parte del control de código fuente VSPackage para habilitar este mecanismo de selección.  
  
### <a name="registry-entries"></a>Entradas del Registro  
 Un paquete de control de código fuente necesita tres GUID privados:  
  
-   GUID del paquete: Este es el GUID principal para el paquete que contiene la implementación de control de código fuente (denominada ID_Package en esta sección).  
  
-   GUID de Control de código fuente: Esto es un GUID para el control de código fuente VSPackage que se usa para registrar con código auxiliar Control de código fuente de Visual Studio y también se utiliza como un contexto de la interfaz de Usuario de comando GUID. El GUID de servicio de control de origen está registrado en el GUID del control de código fuente. En el ejemplo, el GUID del control de código fuente se denomina ID_SccProvider.  
  
-   GUID de servicio de control de origen: se trata del servicio privado GUID utilizado por Visual Studio (denominado SID_SccPkgService en esta sección). Además, el paquete de control de código fuente debe definir el resto de GUID para VSPackages, ventanas de herramientas y así sucesivamente.  
  
 Un control de código fuente VSPackage deben realizarse las siguientes entradas del registro:  
  
|Nombre de clave|Entradas|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(valor predeterminado) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(valor predeterminado) = rg_sz: \< nombre descriptivo del paquete><br /><br /> Servicio = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(valor predeterminado) = rg_sz: #\< Id. de recurso para el nombre localizado><br /><br /> Paquete = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Tenga en cuenta que el nombre de clave, `SourceCodeControl`, ya está usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y no está disponible como una opción para \< PackageName>.)|(valor predeterminado) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Al seleccionar un paquete de Control de código fuente  
 Varias en función de la API de complementos de Control de origen de complementos y VSPackages puede ser registrados simultáneamente el control de código fuente. El proceso de selección de un complemento de control de código fuente o un paquete VSPackage debe asegurarse de que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga el complemento o VSPackage en el momento adecuado y puede diferir la carga componentes innecesarios hasta que son necesarios. Además, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe quitar todas las de la interfaz de Usuario desde otros VSPackages inactivas, incluidos elementos de menú, cuadros de diálogo y barras de herramientas y mostrar la interfaz de Usuario para el paquete de VS activa.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carga un paquete VSPackage del control de código fuente cuando se realiza cualquiera de las siguientes operaciones:  
  
-   Se abre la solución (cuando la solución está bajo control de código fuente).  
  
     Cuando se abre una solución o proyecto bajo control de código fuente, el IDE hace que el control de código fuente VSPackage que designó para que esa solución que se va a cargar.  
  
-   Cualquiera de los comandos de menú del control de código fuente VSPackage se ejecutan.  
  
 Un control de código fuente A que VSPackage debe cargar los componentes que necesita sólo cuando realmente va utiliza (lo que se conoce como la carga retrasada).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>El intercambio automático VSPackage basado en la solución  
 Puede intercambiar manualmente el control de código fuente VSPackages a través de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opciones** cuadro de diálogo en el **Control de código fuente** categoría. El intercambio automático de paquetes basados en soluciones significa que un paquete de control de código fuente que se ha designado para una solución concreta se establece automáticamente en activo cuando se abre esa solución. Debe implementar cada paquete de control de código fuente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Controla el cambio entre ambos del origen de los complementos de control (implementación de la API de complemento de Control de origen) y VSPackages de control de código fuente.  
  
 El paquete de adaptador de Control de origen se utiliza para cambiar a basada en la API de complementos de Control de código fuente cualquier complemento. El proceso de cambio para el paquete intermedio de adaptador de Control de origen y determinar qué complemento de control de código fuente debe establecerse en activo o inactivo es transparente para el usuario. El paquete del adaptador siempre está activo cuando cualquier complemento de control de código fuente está activa. Cambiar entre dos cantidades de complementos de control de origen para simplemente carga y descarga la DLL del complemento. Sin embargo, se cambia a un control de código fuente VSPackage, implica interactuar con el IDE para cargar el VSPackage adecuado.  
  
 Un control de código fuente VSPackage se llama cuando se abre una solución y la clave del registro para el VSPackage está en el archivo de solución. Cuando se abre la solución, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] busca el valor del registro y cargue el control de origen que corresponda VSPackage. Control de código fuente de todos los VSPackages debe tener las entradas del registro que se ha descrito anteriormente. Una solución que se encuentra bajo control de código fuente se marca como está asociado con un control de origen determinado VSPackage. Paquetes VSPackage deben implementar el control de código fuente del <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> para permitir el VSPackage basado en la solución automática intercambio.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Interfaz de Usuario para la selección de paquetes y el cambio de Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proporciona una interfaz de Usuario para el control de código fuente VSPackage y la selección de complemento en el **opciones** cuadro de diálogo en el **Control de código fuente** categoría. Permite al usuario seleccionar el complemento de control de origen activo o el VSPackage. Incluye una lista desplegable:  
  
-   Todos los paquetes de control de código fuente instalado  
  
-   Instalar todos los complementos de control de código fuente  
  
-   Una opción "Ninguno", que deshabilita el control de código fuente  
  
 Solo la interfaz de Usuario para la opción de control de origen activo está visible. La selección de VSPackage oculta la interfaz de Usuario para el VSPackage anterior y muestra la interfaz de Usuario para una nueva. El VSPackage active está activado en cada usuario. Si un usuario tiene varias copias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] abiertos al mismo tiempo, cada uno de ellos podrían utilizar un VSPackage active diferentes. Si varios usuarios inician sesión el mismo equipo, cada usuario puede tener instancias independientes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Abrir, cada uno con un VSPackage active diferentes. Cuando varias instancias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se cierran con un usuario, el control de código fuente VSPackage que estaba activa para la última solución abierta se convierte en el control de código fuente predeterminada VSPackage, establecerse activo en el reinicio.  
  
 A diferencia de las versiones anteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], un reinicio IDE ya no es la única manera de cambiar control de código fuente VSPackages. Selección de VSPackage es automático. Conmutación de paquetes, requiere privilegios de usuario de Windows (no administrador o usuario avanzado).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Características](../../extensibility/internals/source-control-vspackage-features.md)   
 [Crear un Control de código fuente complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)