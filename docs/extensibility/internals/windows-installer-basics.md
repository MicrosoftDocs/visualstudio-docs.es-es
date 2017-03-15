---
title: "Fundamentos de Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Installer, VSPackages"
  - "VSPackages, conceptos básicos de Windows Installer"
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Fundamentos de Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Windows Installer instala y desinstala aplicaciones o productos de software en el equipo del usuario, la realización de estas tareas en unidades denominadas componentes del instalador de Windows \(también conocidos como WICs o simplemente componentes\). Un GUID identifica cada WIC, que es la unidad básica de la instalación y el recuento de referencias para configuraciones mediante Windows Installer.  
  
 Para obtener la documentación completa de Windows Installer, vea el tema de Platform SDK, [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## Creación de un paquete VSPackage  
 Windows Installer utiliza paquetes de instalación, que contienen información que Windows Installer necesita para instalar, desinstalar o reparar un producto y ejecutar la interfaz de usuario \(UI\) de configuración. Cada paquete de instalación incluye un archivo .msi, que contiene una base de datos de la instalación, un flujo de información de resumen y secuencias de datos para distintas partes de la instalación. Para usar el programa de instalación, debe crear una instalación. Porque el instalador organiza las instalaciones en torno al concepto de componentes y almacena información sobre la instalación en una base de datos relacional, el proceso de creación de un paquete de instalación ampliamente implica los pasos siguientes:  
  
1.  Planear la configuración de creación para admitir el control de versiones y estrategias en paralelo.  
  
2.  Identificar las características que se presentará a los usuarios.  
  
3.  Organizar el VSPackage y las dependencias en componentes.  
  
4.  Rellenar con información de la base de datos de instalación.  
  
5.  Validar el paquete de instalación.  
  
 Esta documentación se refiere principalmente a los pasos primeros y terceros del proceso. Durante estos pasos organizar sus características de VSPackage en WICs por lo que también puede enmarcar el control de versiones y atender la estrategia para tener en cuenta las versiones posteriores de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Los tres pasos restantes se tratan detalladamente en la documentación de Windows Installer en Platform SDK.  
  
## Términos clave  
 A continuación se muestran las definiciones de términos clave relacionados con la tecnología de Windows Installer.  
  
 Recurso  
 Archivos, claves del registro, accesos directos, o, y así sucesivamente que puede instalarse en un equipo. Estos recursos se agrupan lógicamente en componentes de Windows Installer.  
  
 Componente de Windows Installer \(WIC\)  
 La unidad básica de instalación que representa una agrupación lógica de los recursos relacionados que se instalan y desinstalan como una unidad. Componentes de Windows Installer se identifican mediante un identificador único de componentes, o un GUID. Además, Windows Installer mantiene su referencia de recuento en el nivel WIC. Para una flexibilidad máxima de control de versiones, incluir no más de un recurso principal, como un archivo DLL, en un determinado WIC. Tenga en cuenta que después de identificar y rellenar un WIC, asígnele un GUID y lo implementa, no puede cambiar su composición. Para obtener más información, consulte [Organizar aplicaciones en componentes](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 \(Paquete redistribuible\)  
 Una unidad de implementación que consta de un archivo .msi y los archivos de origen externo al que puede señalar a este archivo. Un paquete contiene toda la información que necesita Windows Installer para ejecutar la interfaz de usuario y para instalar o desinstalar la aplicación.  
  
 archivo .msi  
 Un archivo de almacenamiento estructurado COM que contiene las instrucciones y los datos necesarios para instalar una aplicación. Cada paquete contiene al menos un archivo MSI. El archivo .msi contiene la base de datos de instalador, una secuencia de información de resumen y posiblemente una o varias transformaciones y los archivos de código fuente interna. Que se instalen archivos pueden se comprimen en un archivador y almacenarse en una secuencia en el archivo .msi o almacenados, comprimidos o descomprimidos, fuera del archivo .msi en el medio de origen. Para obtener más información, consulte [extensiones de archivo de Windows Installer](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## Cumplimiento de las reglas de Windows Installer  
 Dos conjuntos de reglas determinan la implementación de recursos a través de los componentes de la instalación. Se mantiene un conjunto de reglas por Windows Installer, aunque debería exigir el segundo conjunto como autor de la instalación.  
  
> [!NOTE]
>  Aplicación de reglas de Windows Installer se produce sólo si se ejecuta una validación del archivo .msi. No obstante, se les advierte para tratar estas reglas como prácticas recomendadas. Para obtener más información, consulte [validar una base de datos de instalación](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) y [validación del paquete](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### Reglas exigidas por el programa de instalación  
  
-   Todos los archivos de un determinado componente deben instalarse en el mismo directorio. Por el contrario, deben pertenecer archivos instalados en carpetas distintas para separar los componentes.  
  
-   Puede haber sólo una ruta de acceso clave cada componente. La ruta de acceso de clave es simplemente una archivo o clave del registro que representa el componente completo.  
  
#### Responsabilidades del proveedor de componentes  
  
-   Los dos recursos que pueden enviar por separado en las versiones posteriores deben existir en componentes independientes. Los recursos deben estar agrupados en el mismo componente sólo cuando esté seguro de que estos recursos nunca se enviarán por separado. De hecho, se recomienda que todos los recursos principales \(por ejemplo, DLL\) siempre se encuentran en WICs independientes. Para obtener más información, consulte [definir componentes del instalador](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Nunca debe enviar ningún recurso con versiones en WIC más de uno.  
  
## Vea también  
 [¿Qué ocurre si se siguen las reglas de componente?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)