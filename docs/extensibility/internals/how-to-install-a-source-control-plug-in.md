---
title: 'Cómo: instalar un complemento de Control de código fuente | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4ffabd7adf35956163c8744eae6539e96990f38a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-install-a-source-control-plug-in"></a>Cómo: instalar un complemento de Control de código fuente
Crear un control de código fuente complemento implica tres pasos:  
  
1.  Crear un archivo DLL con las funciones definidas en la sección de referencia de API de complemento de Control de origen de esta documentación.  
  
2.  Implemente las funciones definidas por la API de complementos de Control de código fuente. Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] llamadas, disponer de interfaces y cuadros de diálogo desde el complemento.  
  
3.  Registrar el archivo DLL mediante la realización de entradas de registro correspondientes.  
  
## <a name="integration-with-visual-studio"></a>Integración con Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es compatible con complementos de control de código fuente que se ajustan a la API de complemento de Control de origen.  
  
### <a name="registering-the-source-control-plug-in"></a>Registrar el complemento de Control de código fuente  
 Antes de poder llamar un entorno de desarrollo integrado (IDE) está ejecutando en el sistema de control de código fuente, debe buscar primero el origen de la DLL del complemento que exporta la API de control.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Para registrar el origen de controlar la DLL del complemento  
  
1.  Agregue dos entradas bajo la clave HKEY_LOCAL_MACHINE en la subclave SOFTWARE que especifica la subclave de nombre de compañía seguida de la subclave de nombre de producto. El patrón es HKEY_LOCAL_MACHINE\SOFTWARE\\*[nombre de compañía]*\\*[nombre de producto]*\\*[entrada]* = valor. Las dos entradas siempre se llaman SCCServerName y SCCServerPath. Cada uno de ellos es una cadena normal.  
  
     Por ejemplo, si el nombre de la empresa es de Microsoft y el producto de control de código fuente se denomina SourceSafe, esta ruta de acceso del registro sería HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe. En esta subclave, la primera entrada, SCCServerName, es una cadena legible para el usuario que se designa el producto. La segunda entrada, SCCServerPath, es la ruta de acceso completa al origen de controlar la DLL del complemento que se debe conectar el IDE. A continuación proporciona entradas del registro de ejemplo:  
  
    |Entrada de registro de ejemplo|Valor de ejemplo|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  El SCCServerPath es la ruta de acceso completa para el complemento de SourceSafe. El complemento de control de código fuente usará nombres de empresas y productos diferentes pero las mismas rutas de entrada del registro.  
  
2.  Las siguientes entradas de registro opcional pueden utilizarse para modificar el comportamiento de su complemento de control de código fuente. Estas entradas ir en la misma subclave como SccServerName y SccServerPath.  
  
    -   La entrada HideInVisualStudioregistry puede usarse si no desea que el origen de control-plug-de que aparezca en la lista de selección de complemento de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Esta entrada también afectará el cambio automático para el complemento de control de código fuente. Un uso posible para esta entrada es si se proporciona un paquete de control de código fuente que reemplaza el complemento del control de origen pero desea que sea más fácil para el usuario migrar desde mediante el complemento para el paquete de control de código fuente de control de código fuente. Cuando se instala el paquete de control de código fuente, establece esta entrada del registro, que oculta el complemento.  
  
         HideInVisualStudio es un valor DWORD y se establece en 1 para ocultar el complemento o 0 para mostrar el complemento. Si no aparece la entrada del registro, el comportamiento predeterminado es mostrar el complemento.  
  
    -   La entrada de registro DisableSccManager puede usarse para deshabilitar u ocultar el **iniciar \<servidor de Control de origen >** opción de menú que aparece normalmente en el **archivo**  ->   **Control de código fuente** submenú. Al seleccionar este menú opción llamadas el [SccRunScc](../../extensibility/sccrunscc-function.md) (función). El complemento de control de código fuente puede no admitir un programa externo y, por tanto, puede que desee deshabilitar u ocultar incluso la **iniciar** opción de menú.  
  
         DisableSccManager es un valor DWORD se establece en 0 para habilitar la **iniciar \<servidor de Control de origen >** opción de menú, establézcalo en 1 para deshabilitar la opción de menú y se establece en 2 para ocultar la opción de menú. Si no aparece esta entrada del registro, el comportamiento predeterminado es mostrar la opción de menú.  
  
    |Entrada de registro de ejemplo|Valor de ejemplo|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Agregue la subclave SourceCodeControlProvider, bajo la clave HKEY_LOCAL_MACHINE en la subclave SOFTWARE.  
  
     En esta subclave, la entrada del registro ProviderRegKey se establece en una cadena que representa la subclave que se han colocado en el registro en el paso 1. El patrón es HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = SOFTWARE\\*[nombre de compañía]*\\*[nombre de producto]*.  
  
     Éste es el contenido de ejemplo para esta subclave.  
  
    |Entrada del registro|Valor de ejemplo|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  El complemento del control de origen se utiliza la misma subclave y nombres de las entradas, pero el valor será diferente.  
  
4.  Cree una subclave denominada InstalledSCCProviders bajo la subclave SourceCodeControlProvider y, a continuación, colocar una entrada en esa subclave.  
  
     El nombre de esta entrada es el nombre legible para el usuario del proveedor (igual que el valor especificado para la entrada de SCCServerName) y el valor es, una vez más, la subclave que se creó en el paso 1. El patrón es HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[nombre para mostrar]* = SOFTWARE\\*[nombre de compañía]* \\ *[nombre de producto]*.  
  
     Por ejemplo:  
  
    |Entrada de registro de ejemplo|Valor de ejemplo|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Puede haber varios origen control complementos registrados de esta manera. Se trata cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] busca instalar todos los complementos basadas en la API de complemento de Control de origen.  
  
## <a name="how-an-ide-locates-the-dll"></a>Cómo un IDE busca el archivo DLL  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tiene dos formas de buscar el origen de controlan la DLL del complemento:  
  
-   Busque el control de código fuente predeterminada complemento y conectarse a ella de manera silenciosa.  
  
-   Buscar origen registrado todos los complementos de control, desde el que el usuario elige uno.  
  
 Para buscar el archivo DLL en la primera forma, el IDE busca bajo la subclave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider para la entrada ProviderRegKey. El valor de esta entrada apunta a otro subclave. El IDE, a continuación, busca una entrada denominada SccServerPath en esa segunda subclave en HKEY_LOCAL_MACHINE. El valor de esta entrada apunta el IDE al archivo DLL.  
  
> [!NOTE]
>  El IDE no carga archivos DLL de rutas de acceso relativas (por ejemplo,.\NewProvider.DLL). Debe especificarse una ruta de acceso completa al archivo DLL (por ejemplo, c:\Providers\NewProvider.DLL). Esto refuerza la seguridad del IDE evitando la carga de DLL de complemento no autorizadas o suplantadas.  
  
 Para buscar el archivo DLL en la segunda forma, el IDE busca bajo la subclave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders para todas las entradas*.* Cada entrada tiene un nombre y un valor. El IDE muestra una lista de estos nombres para el usuario*.* Cuando el usuario elige un nombre, el IDE busca el valor para el nombre seleccionado que apunta a una subclave. El IDE busca una entrada denominada SccServerPath en esa subclave en HKEY_LOCAL_MACHINE. El valor de esa entrada apunta el IDE al archivo DLL correcta.  
  
 Un complemento de control de código fuente debe admitir las dos formas de encontrar el archivo DLL y, por lo tanto, establezca ProviderRegKey, sobrescribiendo cualquier configuración anterior. Lo que es más importante, debe agregar propio a la lista de InstalledSccProviders para que el usuario puede optar por qué complemento de control de código fuente para usar.  
  
> [!NOTE]
>  Dado que se usa la clave HKEY_LOCAL_MACHINE, complemento de control de solo origen puede registrarse como el control de código fuente predeterminada complemento en un equipo determinado (sin embargo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permite a los usuarios determinar qué complemento de control de código fuente que deseen utilizar realmente para un solución concreta). Durante el proceso de instalación, compruebe para ver si un complemento de control de código fuente ya está configurado; Si es así, pida al usuario si desea establecer el control de código fuente nuevo complemento se instala como el valor predeterminado o no. Durante la desinstalación, no quite otras subclaves del registro que son comunes a todos los complementos código fuente control en HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; quitar sólo la subclave de SCC determinada.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>El modo en que el IDE detecta compatibilidad con la versión 1.2 y 1.3  
 ¿Cómo does [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detectar si una funcionalidad de versión 1.2 y 1.3 de la API de complementos de Control de código fuente de complemento admite? Para declarar funciones avanzadas, el complemento de control de origen debe implementar la función correspondiente.  
  
 En primer lugar, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comprueba el valor devuelto por una llamada a la [SccGetVersion](../../extensibility/sccgetversion-function.md). Debe ser mayor o igual a 1.2.  
  
 Después, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina si se admite la nueva capacidad determinada mediante el examen de la `lpSccCaps` argumento en el [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Si se cumplen ambas condiciones, pueden llamarse las nuevas funciones que se admiten en las versiones 1.2 y 1.3.  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)