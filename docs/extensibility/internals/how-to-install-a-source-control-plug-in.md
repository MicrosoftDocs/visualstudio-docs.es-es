---
title: 'Cómo: instalar un complemento de Control de código fuente | Microsoft Docs'
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
ms.openlocfilehash: b72902813644d887a9bb8e97fc783a48d1c374c7
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511497"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Cómo: instalar un complemento de control de código fuente
Creación de un control de código fuente complemento implica tres pasos:  
  
1.  Cree un archivo DLL con las funciones definidas en la sección de referencia de API de complemento de Control de código fuente de esta documentación.  
  
2.  Implemente las funciones definidas por la API de complemento de Control de código fuente. Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] llamadas, disponer de interfaces y los cuadros de diálogo desde el complemento.  
  
3.  Registrar la DLL mediante la realización de entradas de registro correspondientes.  
  
## <a name="integration-with-visual-studio"></a>Integración con Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite complementos de control de código fuente que se ajustan a la API de complemento de Control de código fuente.  
  
### <a name="register-the-source-control-plug-in"></a>Registrar el complemento de control de código fuente  
 Antes de poder llamar un entorno de desarrollo integrado (IDE) está ejecutando en el sistema de control de código fuente, debe buscar primero el origen de la DLL del complemento que exporta de la API de control.  
  
#### <a name="to-register-the-source-control-plug-in-dll"></a>Para registrar el control de origen al archivo DLL de complemento  
  
1.  Agregue dos entradas en el **HKEY_LOCAL_MACHINE** clave en el **SOFTWARE** subclave que especifica la subclave de nombre de la empresa seguido de la subclave de nombre de producto. El patrón es **HKEY_LOCAL_MACHINE\SOFTWARE\\\<nombre de la compañía >\\\<nombre del producto >\\\<entrada >**  =  *valor*. Siempre se llaman a las dos entradas **SCCServerName** y **SCCServerPath**. Cada uno es una cadena normal.  
  
     Por ejemplo, si el nombre de la empresa es de Microsoft y su producto de control de código fuente se denomina SourceSafe, esta ruta de acceso del registro sería **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. En esta subclave, la primera entrada, **SCCServerName**, es una cadena legible por el usuario de nomenclatura de su producto. La segunda entrada, **SCCServerPath**, es la ruta de acceso completa al origen de controlar la DLL del complemento que debe conectarse el IDE. A continuación proporciona entradas del registro de ejemplo:  
  
    |Entrada de registro de ejemplo|Valor de ejemplo|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|  
  
    > [!NOTE]
    >  SCCServerPath es la ruta de acceso completa para el complemento de SourceSafe. El complemento de control de código fuente usará nombres de empresa y los productos diferentes pero las mismas rutas de entrada del registro.  
  
2.  Las siguientes entradas del registro opcional pueden usarse para modificar el comportamiento de su complemento de control de código fuente. Estas entradas van en la misma subclave como **SccServerName** y **SccServerPath**.  
  
    -   El **HideInVisualStudioregistry** entrada puede usarse si no desea que el origen de control-complemento aparezca en el **selección de complemento** lista de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Esta entrada también afectará el cambio automático para el complemento de control de código fuente. Un uso posible para esta entrada es si proporciona un paquete de control de código fuente que reemplaza el complemento de control de código fuente, pero desea que sea más fácil para el usuario para la migración desde el complemento para el paquete de control de código fuente de control de origen. Cuando se instala el paquete de control de código fuente, establece esta entrada del registro, que oculta el complemento.  
  
         **HideInVisualStudio** es un valor DWORD y se establece en *1* para ocultar el complemento o *0* para mostrar el complemento. Si no aparece la entrada del registro, el comportamiento predeterminado es mostrar el complemento.  
  
    -   El **DisableSccManager** entrada del registro puede usarse para deshabilitar u ocultar el **iniciar \<servidor de Control de código fuente >** opción de menú que aparece normalmente en el **archivo**  >  **Control de código fuente** submenú. Al seleccionar este menú opción llamadas la [SccRunScc](../../extensibility/sccrunscc-function.md) función. El complemento de control de código fuente no puede admitir un programa externo y, por tanto, es posible que desee deshabilitar u ocultar incluso la **iniciar** opción de menú.  
  
         **DisableSccManager** es un valor DWORD y se establece en *0* para habilitar la **iniciar \<servidor de Control de código fuente >** opción de menú, establecida en *1* a Deshabilite la opción de menú y establezca *2* para ocultar la opción de menú. Si no aparece esta entrada del registro, el comportamiento predeterminado es mostrar la opción de menú.  
  
    |Entrada de registro de ejemplo|Valor de ejemplo|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Agregue la subclave, **SourceCodeControlProvider**, en el **HKEY_LOCAL_MACHINE** clave en el **SOFTWARE** subclave.  
  
     En esta subclave, la entrada del registro **ProviderRegKey** se establece en una cadena que representa la subclave que se han colocado en el registro en el paso 1. El patrón es **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *SOFTWARE\\< nombre de la compañía\>\\< nombre de producto \>*.  
  
     El siguiente es el contenido de ejemplo para esta subclave.  
  
    |Entrada del registro|Valor de ejemplo|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  El complemento de control de código fuente se utiliza la misma subclave y nombres de entrada, pero el valor será diferente.  
  
4.  Cree una subclave denominada **InstalledSCCProviders** bajo el **SourceCodeControlProvider** subclave y, a continuación, coloque una entrada en dicha subclave.  
  
     El nombre de esta entrada es el nombre legible por el usuario del proveedor (igual que el valor especificado para la entrada SCCServerName) y el valor es, una vez más, la subclave que se creó en el paso 1. El patrón es **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<display name>** = *SOFTWARE\\< nombre de la compañía\> \\< nombre de producto\>*.  
  
     Por ejemplo:  
  
    |Entrada de registro de ejemplo|Valor de ejemplo|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Puede haber varios origen control complementos registrados de este modo. Se trata cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] busca instalados todos los complementos en función de API de complemento de Control de código fuente.  
  
## <a name="how-an-ide-locates-the-dll"></a>Cómo un IDE busca el archivo DLL  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tiene dos formas de buscar el origen de controlan la DLL del complemento:  
  
-   Busque el control de código fuente predeterminada complemento y conectarse a ella de manera silenciosa.  
  
-   Buscar origen todas las instancias registrada en los complementos de control desde el que el usuario elige uno.  
  
 Para localizar el archivo DLL en la primera de ellas, el IDE busca en el **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** subclave para la entrada **ProviderRegKey**. El valor de esta entrada apunta a otro subclave. El IDE, a continuación, busca una entrada denominada **SccServerPath** en ese segundo subclave bajo **HKEY_LOCAL_MACHINE**. El valor de esta entrada apunta el IDE a la DLL.  
  
> [!NOTE]
>  El IDE no carga los archivos DLL de rutas de acceso relativas (por ejemplo, *.\NewProvider.DLL*). Se debe especificar una ruta de acceso completa al archivo DLL (por ejemplo, *c:\Providers\NewProvider.DLL*). Esto refuerza la seguridad del IDE al impedir la carga de archivos DLL de complemento suplantadas o no autorizadas.  
  
 Para localizar el archivo DLL en la segunda forma, el IDE busca en el **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** subclave para todas las entradas. Cada entrada tiene un nombre y un valor. El IDE muestra una lista de estos nombres al usuario. Cuando el usuario elige un nombre, el IDE busca el valor para el nombre seleccionado en la que apunta a una subclave. El IDE busca una entrada denominada **SccServerPath** en dicha subclave bajo **HKEY_LOCAL_MACHINE**. El valor de esa entrada apunta el IDE a la DLL correcta.  
  
 Un complemento de control de origen debe admitir ambas formas de buscar el archivo DLL y, por lo tanto, establece **ProviderRegKey**, sobrescribiendo cualquier configuración anterior. Más importante aún, debe agregar a la lista de **InstalledSccProviders** por lo que el usuario puede optar por qué complemento de control de código fuente para usar.  
  
> [!NOTE]
>  Dado que el **HKEY_LOCAL_MACHINE** clave se usa, el complemento de control de solo origen se puede registrar como el control de código fuente predeterminada complemento en un equipo determinado (sin embargo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permite a los usuarios a determinar qué complemento de control de código fuente quieren usar para una solución concreta). Durante el proceso de instalación, compruebe si ya está establecido un complemento de control de código fuente; Si es así, pida al usuario si desea establecer el control de código fuente nuevo complemento que se instala como el valor predeterminado o no. Durante la desinstalación, no quite otras subclaves del registro que son comunes a todos los complementos código fuente control en **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; quitar solo la subclave SCC determinada.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Cómo el IDE detecta la compatibilidad con la versión 1.2 o 1.3  
 ¿Cómo does [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detectar si una funcionalidad de versión 1.2 y 1.3 complemento admite API de complemento de Control de código fuente? Para declarar la funcionalidad avanzada, el complemento de control de origen debe implementar la función correspondiente:  
  
 Primero, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comprueba el valor devuelto por una llamada a la [SccGetVersion](../../extensibility/sccgetversion-function.md). Debe ser mayor o igual a la 1.2.  
  
 A continuación, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina si se admite la nueva capacidad determinada examinando el `lpSccCaps` argumento en el [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Si se cumplen ambas condiciones, se pueden llamar a las nuevas funciones compatibles con versiones 1.2 y 1.3.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a los complementos de control de código fuente](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)