---
title: 'Cómo: Instalar un complemento de control de código fuente ( Source Control Plug-in) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707995"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Cómo: Instalar un complemento de control de código fuente
La creación de un complemento de control de código fuente implica tres pasos:

1. Cree un archivo DLL con las funciones definidas en la sección de referencia de la API de complemento de Control de código fuente de esta documentación.

2. Implemente las funciones definidas por la API del complemento de Control de código fuente. Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lo solicite, haga que las interfaces y los cuadros de diálogo estén disponibles desde el complemento.

3. Registre el archivo DLL realizando las entradas de registro adecuadas.

## <a name="integration-with-visual-studio"></a>Integración con Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]admite complementos de control de código fuente que se ajustan a la API de complementode de Control de código fuente.

### <a name="register-the-source-control-plug-in"></a>Registrar el complemento de control de código fuente
 Antes de que un entorno de desarrollo integrado (IDE) en ejecución pueda llamar al sistema de control de código fuente, primero debe buscar el archivo DLL del complemento de control de código fuente que exporta la API.

#### <a name="to-register-the-source-control-plug-in-dll"></a>Para registrar el archivo DLL del complemento de control de código fuente

1. Agregue dos entradas bajo la **clave HKEY_LOCAL_MACHINE** en la subclave SOFTWARE que especifica la subclave **de** nombre de la empresa seguida de la subclave de nombre de producto. El patrón es **HKEY_LOCAL_MACHINE nombre de la empresa de software\\\< \\ \< \\ \<>nombre **de producto>*valor*de entrada> = . Las dos entradas siempre se denominan **SCCServerName** y **SCCServerPath**. Cada uno es una cadena normal.

    Por ejemplo, si el nombre de la empresa es Microsoft y el producto de control de código fuente se denomina SourceSafe, esta ruta de acceso del Registro se **HKEY_LOCAL_MACHINE.** En esta subclave, la primera entrada, **SCCServerName**, es una cadena legible por el usuario que nombra el producto. La segunda entrada, **SCCServerPath**, es la ruta de acceso completa al archivo DLL del complemento de control de código fuente al que debe conectarse el IDE. A continuación se proporcionan entradas de registro de ejemplo:

   |Entrada de registro de ejemplo|Valor de ejemplo|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, SourceSafe, SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, SourceSafe, SCCServerPath|*c:-vss-win32-ssscc.dll*|

   > [!NOTE]
   > SCCServerPath es la ruta de acceso completa al complemento SourceSafe. El complemento de control de código fuente usará diferentes nombres de empresa y producto, pero las mismas rutas de acceso de entrada del Registro.

2. Las siguientes entradas de registro opcionales se pueden usar para modificar el comportamiento del complemento de control de código fuente. Estas entradas van en la misma subclave que **SccServerName** y **SccServerPath**.

   - La entrada **HideInVisualStudioregistry** se puede utilizar si no desea que el complemento de control [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de código fuente aparezca en la lista Selección de **complementos** de . Esta entrada también afectará al cambio automático al complemento de control de código fuente. Un posible uso de esta entrada es si proporciona un paquete de control de código fuente que reemplaza el complemento de control de código fuente, pero desea facilitar al usuario migrar desde el uso del complemento de control de código fuente al paquete de control de código fuente. Cuando se instala el paquete de control de código fuente, establece esta entrada del Registro, que oculta el complemento.

      **HideInVisualStudio** es un valor DWORD y se establece en *1* para ocultar el complemento o *0* para mostrar el complemento. Si la entrada del Registro no aparece, el comportamiento predeterminado es mostrar el complemento.

   - La entrada del Registro **DisableSccManager** se puede usar para deshabilitar u ocultar la opción de menú **Iniciar \<** servidor de control de código fuente>que normalmente aparece en **el** > submenú**Control de código fuente** de archivos. Al seleccionar esta opción de menú se llama a la función [SccRunScc.](../../extensibility/sccrunscc-function.md) Es posible que el complemento de control de código fuente no admita un programa externo y, por lo tanto, es posible que desee deshabilitar u incluso ocultar la opción de menú **Iniciar.**

      **DisableSccManager** es un valor DWORD y se establece en *0* para habilitar la opción de menú Iniciar *2* *1* ** \<** servidor de Control de código fuente>, se establece en 1 para deshabilitar la opción de menú y se establece en 2 para ocultar la opción de menú. Si no aparece esta entrada del Registro, el comportamiento predeterminado es mostrar la opción de menú.

   | Entrada de registro de ejemplo | Valor de ejemplo |
   | - |--------------|
   | HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, SourceSafe, HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE,SOFTWARE, Microsoft, SourceSafe, DisableSccManager | 1 |

3. Agregue la subclave **SourceCodeControlProvider**, en la **clave HKEY_LOCAL_MACHINE** de la subclave **SOFTWARE.**

    Bajo esta subclave, la entrada del Registro **ProviderRegKey** se establece en una cadena que representa la subclave que colocó en el registro en el paso 1. El patrón es **HKEY_LOCAL_MACHINE, SOFTWARE, SourceCodeControlProvider, ProviderRegKey** = *SOFTWARE,\\<nombre\> \\ \>* de la empresa<nombre de producto.

    A continuación se muestra el contenido de ejemplo de esta subclave.

   |Entrada del Registro|Valor de ejemplo|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE,SOFTWARE, SourceCodeControlProvider, ProviderRegKey|SOFTWARE-Microsoft-SourceSafe|

   > [!NOTE]
   > El complemento de control de código fuente usará los mismos nombres de subclave y entrada, pero el valor será diferente.

4. Cree una subclave denominada **InstalledSCCProviders** en la subclave **SourceCodeControlProvider** y, a continuación, coloque una entrada bajo esa subclave.

    El nombre de esta entrada es el nombre legible por el usuario del proveedor (el mismo que el valor especificado para la entrada SCCServerName) y el valor es, una vez más, la subclave creada en el paso 1. El patrón se **HKEY_LOCAL_MACHINE, SOFTWARE,\\ SourceCodeControlProvider,\>InstalledSCCProviders<nombre** = para mostrar SOFTWARE*\\<nombre\> \\ \>* de la empresa<nombre del producto .

    Por ejemplo:

   |Entrada de registro de ejemplo|Valor de ejemplo|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE,SOFTWARE, SourceCodeControlProvider, InstalledSCCProviders, Microsoft Visual SourceSafe|SOFTWARE-Microsoft-SourceSafe|

   > [!NOTE]
   > Puede haber varios complementos de control de código fuente registrados de esta manera. Así es [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] como se encuentran todos los complementos basados en API de source Control instalados.

## <a name="how-an-ide-locates-the-dll"></a>Cómo un IDE localiza el archivo DLL
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tiene dos maneras de encontrar el archivo DLL del complemento de control de código fuente:

- Busque el complemento de control de código fuente predeterminado y conéctese a él de forma silenciosa.

- Busque todos los complementos de control de código fuente registrados, de los que el usuario elige uno.

  Para buscar el archivo DLL de la primera manera, el IDE busca en la subclave **HKEY_LOCAL_MACHINE, Software, SourceCodeControlProvider,** la entrada **ProviderRegKey**. El valor de esta entrada apunta a otra subclave. A continuación, el IDE busca una entrada denominada **SccServerPath** en esa segunda subclave en **HKEY_LOCAL_MACHINE**. El valor de esta entrada apunta el IDE al archivo DLL.

> [!NOTE]
> El IDE no carga archivos DLL desde rutas de acceso relativas (por ejemplo, *.-NewProvider.DLL*). Se debe especificar una ruta de acceso completa al archivo DLL (por ejemplo, *c:-Providers-NewProvider.DLL*). Esto refuerza la seguridad del IDE al impedir la carga de archivos DLL de complementonos o suplantados.

 Para buscar el archivo DLL de la segunda manera, el IDE busca en la **subclave HKEY_LOCAL_MACHINE, Software, SourceCodeControlProvider, InstalledSCCProviders** para todas las entradas. Cada entrada tiene un nombre y un valor. El IDE muestra una lista de estos nombres al usuario. Cuando el usuario elige un nombre, el IDE busca el valor del nombre seleccionado que apunta a una subclave. El IDE busca una entrada denominada **SccServerPath** en esa subclave en **HKEY_LOCAL_MACHINE**. El valor de esa entrada apunta el IDE al archivo DLL correcto.

 Un complemento de control de código fuente debe admitir ambas formas de buscar el archivo DLL y, en consecuencia, establece **ProviderRegKey**, sobrescribiendo cualquier configuración anterior. Lo que es más importante, debe agregarse a la lista de **InstalledSccProviders** para que el usuario pueda tener la opción de qué complemento de control de código fuente usar.

> [!NOTE]
> Dado que se utiliza la **clave de HKEY_LOCAL_MACHINE,** solo se puede registrar un complemento de control [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de código fuente como el complemento de control de código fuente predeterminado en un equipo determinado (sin embargo, permite a los usuarios determinar qué complemento de control de código fuente que desean usar realmente para una solución determinada). Durante el proceso de instalación, compruebe si ya se ha establecido un complemento de control de código fuente; si es así, pregunte al usuario si debe establecer o no el nuevo complemento de control de código fuente que se está instalando como predeterminado. Durante la desinstalación, no quite otras subclaves del Registro que sean comunes a todos los complementos de control de código fuente de **HKEY_LOCAL_MACHINE .** eliminar sólo su subclave SCC en particular.

## <a name="how-the-ide-detects-version-1213-support"></a>Cómo el IDE detecta la compatibilidad con la versión 1.2/1.3
 ¿Cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] detecta si un complemento admite la funcionalidad de la API de complemento de Control de código fuente versión 1.2 y 1.3? Para declarar la capacidad avanzada, el complemento de control de código fuente debe implementar la función correspondiente:

 En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] primer lugar, comprueba el valor devuelto llamando a [SccGetVersion](../../extensibility/sccgetversion-function.md). Debe ser mayor o igual que 1.2.

 A [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] continuación, determina si la nueva funcionalidad `lpSccCaps` concreta se admite examinando el argumento en [SccInitialize](../../extensibility/sccinitialize-function.md).

 Si se cumplen ambas condiciones, se puede llamar a las nuevas funciones admitidas en las versiones 1.2 y 1.3.

## <a name="see-also"></a>Vea también
- [Introducción a los complementos de control de código fuente](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
