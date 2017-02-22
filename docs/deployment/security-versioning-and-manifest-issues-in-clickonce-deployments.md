---
title: "Problemas de seguridad, versiones y manifiestos en implementaciones de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "aplicaciones ClickOnce, problemas con manifiestos"
  - "aplicaciones ClickOnce, temas de seguridad"
  - "aplicaciones ClickOnce, problemas de control de versiones"
  - "aplicaciones ClickOnce, Control de cuentas de usuario de Windows Vista"
  - "manifiestos [ClickOnce]"
  - "seguridad, aplicaciones ClickOnce"
  - "Control de cuentas de usuario, aplicaciones ClickOnce"
  - "control de versiones, aplicaciones ClickOnce"
  - "Windows 7, implementaciones ClickOnce"
  - "Windows Vista, implementaciones ClickOnce"
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Problemas de seguridad, versiones y manifiestos en implementaciones de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay varios problemas relacionados con la seguridad, las versiones de las aplicaciones así como la sintaxis y la semántica de los manifiestos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] debido a los cuales la implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede no realizarse correctamente.  
  
## Control de cuentas de usuario de ClickOnce y Windows Vista  
 En [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], las aplicaciones se ejecutan como un usuario estándar de forma predeterminada, aunque el usuario actual haya iniciado una sesión con una cuenta que tiene permisos de administrador.  Si una aplicación debe realizar una acción que requiere permisos de administrador, se lo indica al sistema operativo que, a continuación, pide al usuario que escriba sus credenciales de administrador.  Esta característica, que se denomina Control de cuentas de usuario \(UAC\), evita que las aplicaciones realicen modificaciones que puedan afectar a todo el sistema operativo sin la aprobación explícita de un usuario.  Las aplicaciones Windows declaran que requieren esta elevación de permisos especificando el atributo `requestedExecutionLevel` en la sección `trustInfo` de su manifiesto de aplicación.  
  
 Debido al riesgo de exposición de las aplicaciones a ataques de elevación de la seguridad, las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no pueden solicitar la elevación de permisos si UAC está habilitado para el cliente.  Cualquier aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que intente establecer su atributo `requestedExecutionLevel` en `requireAdministrator` o `highestAvailable` no se instalará en [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  
  
 En algunos casos, la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podría intentar ejecutarse con permisos de administrador debido a la lógica de detección del instalador en [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  En este caso, puede establecer el atributo `requestedExecutionLevel` en `asInvoker`, en el manifiesto de aplicación.  Esto hará que la propia aplicación se ejecute sin la elevación. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] agrega automáticamente este atributo a todos los manifiestos de aplicación.  
  
 Si está desarrollando una aplicación que requiere permisos de administrador para la duración completa de la aplicación, debería considerar la posibilidad de implementar la aplicación mediante la tecnología de Windows Installer \(MSI\).  Para obtener más información, vea [Fundamentos de Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## Cuotas de aplicaciones en línea y aplicaciones de confianza parcial  
 Si la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se ejecuta en línea en lugar de ejecutarse por medio de una instalación, deberá ajustarse a la cuota reservada para las aplicaciones en línea.  Además, una aplicación de red que se ejecuta con confianza parcial, como un conjunto restringido de permisos de seguridad, no puede superar la mitad del tamaño de cuota.  
  
 Para obtener más información e instrucciones sobre cómo cambiar la cuota de aplicaciones en línea, vea [Información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## Problemas de versiones  
 Pueden surgir problemas si se asignan nombres seguros al ensamblado y se incrementa el número de versión del ensamblado para reflejar una actualización de la aplicación.  Cualquier ensamblado que se haya compilado con una referencia a un ensamblado de nombre seguro deberá volver a compilarse por sí mismo; de lo contrario, el ensamblado intentará hacer referencia a la versión anterior.  Esto es debido a que el ensamblado utiliza el valor de versión anterior en su solicitud de enlace.  
  
 Por ejemplo, supongamos que dispone de un ensamblado con nombre seguro en su propio proyecto con la versión 1.0.0.0.  Tras compilar el ensamblado, lo agrega como referencia al proyecto que contiene la aplicación principal.  Si actualiza el ensamblado, incrementa la versión a 1.0.0.1 e intenta implementarlo sin volver a compilar también la aplicación, ésta no podrá cargar el ensamblado en tiempo de ejecución.  
  
 Este error sólo puede producirse si edita manualmente los manifiestos de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]; este error no debe producirse si genera la implementación mediante [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## Especificar ensamblados de .NET Framework individuales en el manifiesto  
 La aplicación no se cargará si ha editado manualmente una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para hacer referencia a una versión anterior de un ensamblado de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Por ejemplo, si agregase una referencia al ensamblado System.Net para una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anterior a la versión especificada en el manifiesto, se produciría un error.  En general, no debería intentar especificar referencias a ensamblados individuales de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ya que la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en la que se ejecuta la aplicación se especifica como una dependencia en el manifiesto de aplicación.  
  
## Problemas de análisis de manifiesto  
 Los archivos de manifiesto utilizados por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] son archivos XML válidos y con un formato correcto: deben seguir las reglas de sintaxis de XML y utilizar únicamente los elementos y atributos definidos en el esquema XML correspondiente.  
  
 Seleccionar un nombre para la aplicación que contenga un carácter especial, como comillas simples o dobles, puede producir problemas en un archivo de manifiesto.  El nombre de la aplicación forma parte de su identidad de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Actualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no analiza las identidades que contienen caracteres especiales.  Si se produce un error al activar la aplicación, asegúrese de que sólo esté utilizando caracteres alfabéticos y numéricos para el nombre e intente realizar de nuevo la implementación.  
  
 Si ha editado manualmente la implementación o los manifiestos de aplicación, puede haberlos dañado involuntariamente.  Un manifiesto dañado impedirá la instalación correcta de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Puede depurar este tipo de errores en tiempo de ejecución haciendo clic en **Detalles** en el cuadro de diálogo **Error de ClickOnce** y leyendo el mensaje de error del registro.  El registro mostrará uno de los mensajes siguientes:  
  
-   Una descripción del error de sintaxis así como el número de línea y la posición de carácter donde aparece el error.  
  
-   El nombre de un elemento o atributo cuya utilización infringe el esquema del manifiesto.  Si ha agregado manualmente XML a los manifiestos, tendrá que comparar la información agregada con los esquemas del manifiesto.  Para obtener más información, vea [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) y [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
-   Un conflicto de identificadores.  Las referencias de dependencias en los manifiestos de implementación y aplicación deben ser únicas en los atributos `name` y `publicKeyToken`.  Si ambos atributos coinciden con dos elementos cualesquiera de un manifiesto, no se podrá realizar el análisis del manifiesto.  
  
## Precauciones cuando se cambian manualmente manifiestos o aplicaciones  
 Cuando actualiza un manifiesto de aplicación, debe volver a firmar tanto el manifiesto de aplicación como el manifiesto de implementación.  El manifiesto de implementación contiene una referencia al manifiesto de aplicación que incluye el código hash de ese archivo y su firma digital.  
  
### Precauciones con respecto al uso de deploymentProvider  
 El manifiesto de implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tiene una propiedad `deploymentProvider` que señala la ruta de acceso completa a la ubicación desde donde se debe instalar y atender la aplicación:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Esta ruta de acceso se establece cuando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea la aplicación y es obligatoria para las aplicaciones instaladas.  La ruta de acceso indica la ubicación estándar desde donde el instalador de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalará la aplicación y buscará las actualizaciones.  Si utiliza el comando **xcopy** para copiar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en otra ubicación pero no cambia la propiedad `deploymentProvider`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] seguirá haciendo referencia a la ubicación original cuando intente descargar la aplicación.  
  
 Si desea mover o copiar una aplicación, debe actualizar también la ruta de acceso de `deploymentProvider`, de modo que el cliente se instala realmente desde la nueva ubicación.  La actualización de esta ruta de acceso es sobre todo importante si hay aplicaciones instaladas.  Para las aplicaciones en línea que se inician siempre a través de la dirección URL original, la configuración de `deploymentProvider` es opcional.  Si se configura `deploymentProvider`, se tendrá en cuenta; en caso contrario, se utilizará la dirección URL usada para activar la aplicación como dirección URL base para descargar los archivos de aplicación.  
  
> [!NOTE]
>  Cada vez que actualiza el manifiesto, también debe volver a firmarlo.  
  
## Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)