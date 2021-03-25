---
title: 'Cómo: instalar un complemento de control de código fuente | Microsoft Docs'
description: Obtenga información sobre cómo instalar un complemento de control de código fuente en Visual Studio mediante la integración con la API del complemento de control de código fuente de Visual Studio y el registro de la DLL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a0798cb7763ff2766d2de2bb00a80759be8fd3e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078817"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Cómo: instalar un complemento de control de código fuente
La creación de un complemento de control de código fuente implica tres pasos:

1. Cree un archivo DLL con las funciones definidas en la sección referencia de la API del complemento de control de código fuente de esta documentación.

2. Implemente las funciones definidas por la API del complemento de control de código fuente. Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] llama a este, hace que las interfaces y los cuadros de diálogo estén disponibles en el complemento.

3. Registre el archivo DLL mediante las entradas adecuadas del registro.

## <a name="integration-with-visual-studio"></a>Integración con Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite complementos de control de código fuente que se ajustan a la API del complemento de control de código fuente.

### <a name="register-the-source-control-plug-in"></a>Registrar el complemento de control de código fuente
 Antes de que un entorno de desarrollo integrado (IDE) en ejecución pueda llamar al sistema de control de código fuente, primero debe encontrar el archivo DLL del complemento de control de código fuente que exporta la API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Para registrar el archivo DLL del complemento de control de código fuente

1. Agregue dos entradas en la clave **HKEY_LOCAL_MACHINE** en la subclave **software** que especifica la subclave Company Name seguida de la subclave Product Name. El patrón es **\\ \<company name> \\ \<product name>HKEY_LOCAL_MACHINE\SOFTWARE\\ valor \<entry>**  =  . Las dos entradas siempre se denominan **SCCServerName** y **SCCServerPath**. Cada es una cadena normal.

    Por ejemplo, si el nombre de su empresa es Microsoft y el producto de control de código fuente se denomina SourceSafe, esta ruta de acceso del registro sería **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. En esta subclave, la primera entrada, **SCCServerName**, es una cadena legible por el usuario que nombra el producto. La segunda entrada, **SCCServerPath**, es la ruta de acceso completa al archivo DLL del complemento de control de código fuente al que debe conectarse el IDE. A continuación se proporcionan entradas del registro de ejemplo:

   |Entrada del registro de ejemplo|Valor de ejemplo|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > SCCServerPath es la ruta de acceso completa al complemento de SourceSafe. El complemento de control de código fuente usará distintos nombres de compañía y producto, pero las mismas rutas de acceso de entrada del registro.

2. Se pueden usar las siguientes entradas opcionales del registro para modificar el comportamiento del complemento de control de código fuente. Estas entradas van en la misma subclave que **SccServerName** y **SccServerPath**.

   - La entrada **HideInVisualStudioregistry** se puede usar si no desea que el complemento de control de código fuente aparezca en la lista de **selección de complemento** de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Esta entrada también afectará al cambio automático en el complemento de control de código fuente. Un uso posible para esta entrada es si proporciona un paquete de control de código fuente que reemplace el complemento de control de código fuente, pero desea facilitar la migración del usuario mediante el complemento de control de código fuente al paquete de control de código fuente. Cuando se instala el paquete de control de código fuente, se establece esta entrada del registro, que oculta el complemento.

      **HideInVisualStudio** es un valor DWORD y se establece en *1* para ocultar el complemento o en *0* para que se muestre el complemento. Si no aparece la entrada del registro, el comportamiento predeterminado es mostrar el complemento.

   - La entrada del registro **DisableSccManager** se puede usar para deshabilitar u ocultar la opción de menú **Inicio \<Source Control Server>** que normalmente aparece en el   >  submenú **control de código fuente** del archivo. Al seleccionar esta opción de menú, se llama a la función [SccRunScc](../../extensibility/sccrunscc-function.md) . Es posible que el complemento de control de código fuente no sea compatible con un programa externo y, por tanto, puede que desee deshabilitar o incluso ocultar la opción de menú **iniciar** .

      **DisableSccManager** es un valor DWORD y se establece en *0* para habilitar la opción de menú **iniciar \<Source Control Server>** , establézcalo en *1* para deshabilitar la opción de menú y establezca en *2* para ocultar la opción de menú. Si no aparece esta entrada del registro, el comportamiento predeterminado es mostrar la opción de menú.

   | Entrada del registro de ejemplo | Valor de ejemplo |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Agregue la subclave **SourceCodeControlProvider**, en la clave **HKEY_LOCAL_MACHINE** en la subclave **software** .

    En esta subclave, la entrada del registro **ProviderRegKey** se establece en una cadena que representa la subclave que se colocó en el registro en el paso 1. El patrón es **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey**  =  *software \\<nombre de la compañía \> \\<\> nombre del producto*.

    A continuación se muestra el contenido de ejemplo para esta subclave.

   |Entrada del Registro|Valor de ejemplo|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > El complemento de control de código fuente usará la misma subclave y los mismos nombres de entrada, pero el valor será diferente.

4. Cree una subclave denominada **InstalledSCCProviders** en la subclave **SourceCodeControlProvider** y, a continuación, coloque una entrada bajo esa subclave.

    El nombre de esta entrada es el nombre legible para el usuario del proveedor (igual que el valor especificado para la entrada SCCServerName) y el valor es, una vez más, la subclave creada en el paso 1. El patrón es **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<\>** nombre para mostrar software<nombre de la  =  *\\ compañía \> \\<nombre \> del producto*.

    Por ejemplo:

   |Entrada del registro de ejemplo|Valor de ejemplo|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|

   > [!NOTE]
   > Puede haber varios complementos de control de código fuente registrados de esta manera. Así es como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encuentra todos los complementos basados en la API del complemento de control de código fuente instalado.

## <a name="how-an-ide-locates-the-dll"></a>Cómo localiza un IDE el archivo DLL
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tiene dos maneras de buscar el archivo DLL del complemento de control de código fuente:

- Busque el complemento de control de código fuente predeterminado y conéctese a él de forma silenciosa.

- Busca todos los complementos de control de código fuente registrados, desde los que el usuario elige uno.

  Para buscar el archivo DLL de la primera manera, el IDE busca en la subclave **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** de la entrada **ProviderRegKey**. El valor de esta entrada apunta a otra subclave. A continuación, el IDE busca una entrada denominada **SccServerPath** en esa segunda subclave en **HKEY_LOCAL_MACHINE**. El valor de esta entrada apunta el IDE al archivo DLL.

> [!NOTE]
> El IDE no carga los archivos dll desde las rutas de acceso relativas (por ejemplo, *.\NewProvider.DLL*). Se debe especificar una ruta de acceso completa al archivo DLL (por ejemplo, *c:\Providers\NewProvider.DLL*). Esto fortalece la seguridad del IDE al impedir la carga de archivos dll de complementos no autorizados o suplantados.

 Para buscar el archivo DLL de la segunda manera, el IDE busca todas las entradas en la subclave **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** . Cada entrada tiene un nombre y un valor. El IDE muestra al usuario una lista de estos nombres. Cuando el usuario elige un nombre, el IDE busca el valor del nombre seleccionado que apunta a una subclave. El IDE busca una entrada denominada **SccServerPath** en esa subclave en **HKEY_LOCAL_MACHINE**. El valor de esa entrada apunta el IDE a la DLL correcta.

 Un complemento de control de código fuente debe admitir ambas maneras de buscar el archivo DLL y, por consiguiente, establece **ProviderRegKey**, sobrescribiendo cualquier valor anterior. Lo que es más importante, debe agregarse a la lista de **InstalledSccProviders** para que el usuario pueda elegir el complemento de control de código fuente que se va a usar.

> [!NOTE]
> Dado que se usa la clave **HKEY_LOCAL_MACHINE** , solo se puede registrar un complemento de control de código fuente como el complemento de control de código fuente predeterminado en un equipo determinado (sin embargo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permite a los usuarios determinar qué complemento de control de código fuente desean usar realmente para una solución determinada). Durante el proceso de instalación, compruebe si ya se ha establecido un complemento de control de código fuente; Si es así, pregunte al usuario si desea establecer o no el complemento de control de código fuente que se va a instalar como predeterminado. Durante la desinstalación, no quite otras subclaves del registro que sean comunes a todos los complementos de control de código fuente en **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; Quite solo su subclave SCC determinada.

## <a name="how-the-ide-detects-version-1213-support"></a>Cómo detecta el IDE la compatibilidad con la versión 1.2/1.3
 ¿Cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detecta si un complemento admite la funcionalidad de la API del complemento de control de código fuente versión 1,2 y 1,3? Para declarar la funcionalidad avanzada, el complemento de control de código fuente debe implementar la función correspondiente:

 En primer lugar, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comprueba el valor devuelto mediante una llamada a [SccGetVersion](../../extensibility/sccgetversion-function.md). Debe ser mayor o igual que 1,2.

 A continuación, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina si se admite la nueva funcionalidad determinada mediante el examen del `lpSccCaps` argumento en el [SccInitialize](../../extensibility/sccinitialize-function.md).

 Si se cumplen estas dos condiciones, se puede llamar a las nuevas funciones admitidas en las versiones 1,2 y 1,3.

## <a name="see-also"></a>Consulte también
- [Introducción a los complementos de control de código fuente](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
