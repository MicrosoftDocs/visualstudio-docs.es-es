---
title: Agregar referencias usando NuGet en lugar de un SDK de extensión
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a895124effa8155ab2edb4652962b605926234d5
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349483"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Incorporación de referencias usando NuGet en lugar de un SDK de extensión

Puede proporcionar un paquete para su uso en proyectos de Visual Studio mediante NuGet o un kit de desarrollo de software (SDK). Al describir las similitudes y las diferencias entre los dos mecanismos, este artículo puede ayudar a elegir el mejor para una tarea.

- NuGet es un sistema de administración de paquetes de código abierto que simplifica el proceso de incorporar bibliotecas a una solución de proyecto. Para obtener más información, vea la [documentación de NuGet](/nuget).

- Un SDK es una colección de archivos que Visual Studio trata como un único elemento de referencia. En el cuadro de diálogo **Administrador de referencias** se muestran todos los SDK que son pertinentes para el proyecto que está abierto cuando se muestra el cuadro de diálogo. Cuando se agrega un SDK a un proyecto, puede tener acceso a todo el contenido de ese SDK a través de IntelliSense, el **Cuadro de herramientas**, los diseñadores, el **Examinador de objetos**, MSBuild, la implementación, la depuración y el empaquetado. Para obtener más información sobre los SDK, vea [Crear un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>¿Qué mecanismo debo usar?

La tabla siguiente le ayuda a comparar las características de referencia de un SDK con las características de referencia de NuGet.

| Característica | Compatibilidad con el SDK | Notas del SDK | Compatibilidad con NuGet | Notas de NuGet |
| - | - | - |---------------| - |
| El mecanismo hace referencia a una entidad y, después, todos los archivos y funcionalidades están disponibles. | Y | Para agregar un SDK, use el cuadro de diálogo **Administrador de referencias**. Todos los archivos y funcionalidades están disponibles durante el flujo de trabajo de desarrollo. | Y | |
| MSBuild consume automáticamente ensamblados y archivos de metadatos de Windows (*.winmd*). | Y | Las referencias del SDK se pasan automáticamente al compilador. | Y | |
| MSBuild consume automáticamente los archivos .h o .lib. | Y | El archivo *nombreDeSDK.props* indica a Visual Studio cómo configurar el directorio de Visual C++, etc., para el consumo automático de archivos *.h* o *.lib*. | N | |
| MSBuild consume automáticamente los archivos *.js* o *.css*. | Y | En el **Explorador de soluciones**, puede expandir el nodo de referencia de SDK de JavaScript para mostrar archivos individuales *.js* o *.css* y, después, generar etiquetas `<source include/>` arrastrando esos archivos a sus archivos de origen. El SDK es compatible con F5 y con la instalación de paquetes automática. | Y | |
| MSBuild agrega automáticamente el control en el **Cuadro de herramientas**. | Y | El **Cuadro de herramientas** puede consumir SDK y mostrar controles en las pestañas que especifique. | N | |
| El mecanismo admite el instalador de Visual Studio para extensiones (VSIX). | Y | VSIX tiene un manifiesto y lógica especiales para crear paquetes de SDK. | Y | VSIX se puede insertar en otro programa de instalación. |
| El **Examinador de objetos** enumera las referencias. | Y | El **Examinador de objetos** obtiene automáticamente la lista de referencias de los SDK y las enumera. | N | |
| Los archivos y los vínculos se agregan automáticamente al cuadro de diálogo **Administrador de referencias** (los vínculos de ayuda, etc., se rellenan automáticamente). | Y | En el cuadro de diálogo **Administrador de referencias** se enumeran automáticamente los SDK, junto con los vínculos de ayuda y la lista de dependencias de SDK. | N | NuGet proporciona su propio cuadro de diálogo **Administrar paquetes NuGet**. |
| El mecanismo admite varias arquitecturas. | Y | Los SDK pueden incluir varias configuraciones. MSBuild consume los archivos adecuados para cada configuración de proyecto. | N | |
| El mecanismo admite varias configuraciones. | Y | Los SDK pueden incluir varias configuraciones. En función de la arquitectura del proyecto, MSBuild consume los archivos adecuados para cada arquitectura de proyecto. | N | |
| El mecanismo puede especificar "no para la copia". | Y | En función de si se quitan los archivos de la carpeta *\redist* o *\designtime*, puede controlar qué archivos se copian en el paquete de la aplicación de consumo. | N | Debe declarar qué archivos se copian en el manifiesto del paquete. |
| El contenido aparece en archivos localizados. | Y | Los documentos XML localizados de los SDK se incluyen automáticamente para ofrecer una mejor experiencia en tiempo de diseño. | N | |
| MSBuild admite el consumo de varias versiones de un SDK simultáneamente. | Y | El SDK admite el consumo de varias versiones simultáneamente. | N | Esto no es equivalente a hacer referencia. No puede tener a la vez más de una versión de archivos NuGet en el proyecto. |
| El mecanismo admite la especificación de plataformas de destino aplicables, versiones de Visual Studio y tipos de proyectos. | Y | En el cuadro de diálogo **Administrador de referencias** y en el **Cuadro de herramientas** solo se muestran los SDK que se aplican a un proyecto, para que los usuarios puedan elegir más fácilmente los SDK adecuados. | Y (parcialmente) | Pivot es la plataforma de destino. No hay filtrado en la interfaz de usuario. Durante la instalación, podría devolver un error. |
| El mecanismo admite la especificación de información de registro para archivos WinMD nativos. | Y | Puede especificar la correlación entre el archivo .winmd y el archivo .dll en *SDKManifest.xml*. | N | |
| El mecanismo admite la especificación de dependencias en otros SDK. | Y | El SDK solo notifica al usuario, y este debe instalarlos y hacer referencia a ellos de forma manual. | Y | NuGet los extrae automáticamente, sin que se notifique al usuario. |
| El mecanismo se integra con conceptos de la [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], como el manifiesto de la aplicación y el identificador del marco de trabajo. | Y | El SDK debe pasar conceptos específicos de la [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] para que el empaquetado y F5 funcionen correctamente con los SDK que están disponibles en la [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | N | |
| El mecanismo se integra con la canalización de depuración de aplicaciones para aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. | Y | El SDK debe pasar conceptos específicos de la [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] para que el empaquetado y F5 funcionen correctamente con los SDK que están disponibles en la [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | Y | El contenido de NuGet pasa a formar parte del proyecto. No se necesita ninguna consideración especial de F5. |
| El mecanismo se integra con los manifiestos de la aplicación. | Y | El SDK debe pasar conceptos específicos de la [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] para que el empaquetado y F5 funcionen correctamente con los SDK que están disponibles en la [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]. | Y | El contenido de NuGet pasa a formar parte del proyecto. No se necesita ninguna consideración especial de F5. |
| El mecanismo implementa archivos que no son de referencia (por ejemplo, el marco de pruebas de implementación en el que se ejecutan pruebas de aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]). | Y | Si coloca los archivos en la carpeta *\redist*, se implementan automáticamente. | Y | |
| El mecanismo agrega automáticamente los SDK de plataforma en el IDE de Visual Studio. | Y | Si coloca el SDK de [!INCLUDE[win8](../debugger/includes/win8_md.md)] o el SDK de Windows Phone en una ubicación específica con un diseño específico, el SDK se integra automáticamente con todas las características de Visual Studio. | N | |
| El mecanismo admite una máquina de desarrollo limpia. (Es decir, no se requiere ninguna instalación, y funcionará una sencilla recuperación del control de código fuente). | N | Dado que hace referencia a un SDK, debe proteger la solución y el SDK por separado. Puede proteger el SDK desde las dos ubicaciones predeterminadas que no son del Registro desde las que MSBuild itera los SDK (para obtener más información, vea [Crear un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)). Como alternativa, si una ubicación personalizada consta de los SDK, puede especificar el código siguiente en el archivo de proyecto:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Después, proteja los SDK en dicha ubicación. | Y | Puede desproteger la solución y Visual Studio reconocerá inmediatamente los archivos y actuará sobre ellos. |
| Puede unirse a una gran comunidad existente de autores de paquetes. | N/D | La comunidad es nueva. | Y | |
| Puede unirse a una gran comunidad existente de consumidores de paquetes. | N/D | La comunidad es nueva. | Y | |
| Puede unirse a un ecosistema de asociados (galerías personalizadas, repositorios, etc.). | N/D | Los repositorios disponibles incluyen Visual Studio Marketplace, el Centro de descarga de Microsoft y la [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. | Y | |
| El mecanismo se integra con los servidores de compilación de integración continua para la creación y el consumo de paquetes. | Y | El SDK debe pasar la ubicación protegida (propiedad SDKReferenceDirectoryRoot) en la línea de comandos a MSBuild. | Y | |
| El mecanismo admite las versiones de paquete preliminar y estable. | Y | El SDK admite la adición de referencias a varias versiones. | Y | |
| El mecanismo admite la actualización automática de los paquetes instalados. | Y | Si se incluye como VSIX o como parte de las actualizaciones automáticas de Visual Studio, el SDK proporciona notificaciones automáticas. | Y | |
| El mecanismo contiene un archivo *.exe* independiente para crear y consumir paquetes. | Y | El SDK contiene *MSBuild.exe*. | Y | |
| Los paquetes se pueden proteger en el control de versiones. | Y | No se puede proteger nada fuera del nodo Documentos, lo que significa que los SDK de extensión podrían no estar protegidos. El SDK de extensión podría tener un gran tamaño. | Y | |
| Puede usar una interfaz de PowerShell para crear y consumir paquetes. | Y (consumo), N (creación) | No hay herramientas para crear un SDK. El consumo ejecuta MSBuild en la línea de comandos. | Y | |
| Puede usar un paquete de símbolos para la compatibilidad con la depuración. | Y | Si quita los archivos *.pdb* del SDK, los archivos se recogen automáticamente. | Y | |
| El mecanismo admite las actualizaciones automáticas del administrador de paquetes. | N/D | El SDK se revisa con MSBuild. | Y | |
| El mecanismo admite un formato de manifiesto ligero. | Y | *SDKManifest.xml* admite muchos atributos, pero normalmente solo es necesario un pequeño subconjunto. | Y | |
| El mecanismo está disponible para todas las ediciones de Visual Studio. | Y | El SDK es compatible con todas las ediciones de Visual Studio. | Y | NuGet es compatible con todas las ediciones de Visual Studio. |
| El mecanismo está disponible para todos los tipos de proyecto. | N | El SDK admite las aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] a partir de [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. | N | Puede revisar una lista de los proyectos permitidos. |

## <a name="see-also"></a>Vea también

- [Administración de referencias en un proyecto](../ide/managing-references-in-a-project.md)
- [Administrar referencias en un proyecto (Visual Studio para Mac)](/visualstudio/mac/managing-references-in-a-project)