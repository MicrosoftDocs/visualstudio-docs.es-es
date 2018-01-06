---
title: "Desarrollo de mejores prácticas para COM, VSTO y VBA complementos de Office | Documentos de Microsoft"
ms.custom: 
ms.date: 07/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: 
helpviewer_keywords: 
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2158
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8985b3bb6e20b24b86174286104158c8830de971
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="development-best-practices-for-com-vsto-and-vba--add-ins-in-office"></a>Prácticas recomendadas de desarrollo de COM, VSTO y VBA complementos de Office
  Si va a desarrollar complementos COM VSTO y VBA para Office, siga las prácticas recomendadas de desarrollo descritas en este artículo.   Esto le ayudará a garantizar:

-  Compatibilidad de complementos a través de diferentes versiones y las implementaciones de Office.
-  Complejidad reducida de implementación del complemento para los usuarios y los administradores de TI.
-  No se producen errores imprevistos de instalación o en tiempo de ejecución del complemento.

>Nota: El uso de la [Desktop puente](/windows/uwp/porting/desktop-to-uwp-root) para preparar su COM, VSTO o VBA complemento para la tienda Windows no es compatible. Complementos COM, VSTO y VBA no se pueden distribuir en la tienda Windows o la tienda Office. 
  
## <a name="do-not-check-for-office-during-installation"></a>No se comprueban para Office durante la instalación  
 No se recomienda tener el complemento de detectar si Office se instala durante el proceso de instalación del complemento. Si Office no está instalado, puede instalar el complemento y el usuario podrá tener acceso a él después de instalar Office. 
  
## <a name="use-embedded-interop-types-nopia"></a>Usar tipos de interoperabilidad insertados (NoPIA)  
Si la solución utiliza .NET 4.0 o una versión posterior, utilice tipos de interoperabilidad incrustados (NoPIA) en lugar de según el Office interoperabilidad primario ensamblados (PIA) redistribuible. Con la incrustación de tipos reduce el tamaño de la instalación de la solución y garantiza la compatibilidad con versiones posterior. Office 2010 fue la última versión de Office que se incluye el paquete redistribuible de PIA. Para obtener más información, consulte [Tutorial: incrustar información de tipos de ensamblados de Microsoft Office](https://msdn.microsoft.com/en-us/library/ee317478.aspx) y [equivalencia de tipos y tipos de interoperabilidad incrustados](/windows/uwp/porting/desktop-to-uwp-root).

Si la solución utiliza una versión anterior de. NET, se recomienda que actualice la solución para usar .NET 4.0 o posterior. Con .NET 4.0 o posterior, reduce los requisitos previos de tiempo de ejecución en las versiones más recientes de Windows.
  
## <a name="avoid-depending-on-specific-office-versions"></a>Evitar depender de versiones específicas de Office  
Si la solución usa la funcionalidad que sólo está disponible en las versiones más recientes de Office, compruebe que existe la posibilidad de (si es posible, en el nivel de característica) en tiempo de ejecución (por ejemplo, con excepción de control o mediante la comprobación de la versión). Validar las versiones mínimas, en lugar de versiones específicas, mediante las API compatibles en el modelo de objetos, como el [Application.Version propiedad](https://msdn.microsoft.com/en-us/library/office/microsoft.office.interop.excel._application.version.aspx). No se recomienda que depende de metadatos binaria de Office, las rutas de acceso de instalación o las claves del registro porque se puede cambiar entre las instalaciones, los entornos y versiones.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Habilitar el uso de Office de 32 bits y 64 bits   
El destino de compilación predeterminado debe admitir (x86) 32 bits y 64 bits (x64), a menos que la solución depende de las bibliotecas que solo están disponibles para un valor de bits específico. La versión de 64 bits de Office está aumentando de adopción, especialmente en entornos de grandes cantidades de datos. Compatibles con 32 bits y 64 bits facilita a los usuarios para realizar la transición entre las versiones de 32 bits y 64 bits de Office.

Al escribir código VBA, safe de 64 bits de uso instrucciones declare y convertir variables según corresponda. Además, asegúrese de que los documentos pueden compartirse entre los usuarios que ejecutan versiones de 32 bits o 64 bits de Office al proporcionar código para cada valor de bits. Para obtener más información, consulte [Visual Basic de 64 bits para información general sobre aplicaciones](https://msdn.microsoft.com/en-us/library/office/gg264421.aspx).

## <a name="support-restricted-environments"></a>Admitir entornos restringidos   
La solución no debería requerir privilegios de administrador o de elevación de la cuenta de usuario. Además, la solución no debe depender establecer o modificar:

- El directorio de trabajo actual.
- Directorios de la carga DLL.
- La variable de ruta de acceso.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Cambiar la operación de guardar la ubicación de datos compartidos y opciones
Si la solución consta de un complemento y un proceso que es externo a Office, no utilice el registro o la carpeta de datos de aplicación del usuario para el intercambio de datos o la configuración entre el complemento y el proceso externo. En su lugar, considere el uso de la carpeta temporal del usuario, la carpeta documentos o el directorio de instalación de la solución.

## <a name="increment-the-version-number-with-each-update"></a>Incrementar el número de versión con cada actualización
Establecer el número de versión de los archivos binarios de la solución y aumentará con cada actualización. Así resultará más fácil para los usuarios a identificar los cambios entre las versiones y a evaluar la compatibilidad.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Proporcionar instrucciones de compatibilidad para las versiones más recientes de Office
Los clientes están solicitando ISV para proporcionar instrucciones de compatibilidad para sus COM, VSTO y VBA complementos que se ejecutan en Office. Enumerar los compatibilidad explícita con instrucciones ayuda a los clientes que usan Office 365 ProPlus herramientas de preparación para comprender el soporte técnico. 

Para proporcionar instrucciones de compatibilidad para aplicaciones de cliente de Office (por ejemplo, Word o Excel), primero compruebe que los complementos ejecutan en la versión actual de Office y, a continuación, confirmación para proporcionar actualizaciones si su complemento interrumpe la ejecución en una versión futura. No es necesario que probar el complemento cuando Microsoft publica una nueva compilación o una actualización de Office. Microsoft apenas si cambia la plataforma de extensibilidad de COM, VSTO y VBA en Office y se documentará también estos cambios.

>Importante: Microsoft mantiene una lista de complementos compatibles para los informes de disponibilidad y la información de contacto de ISV. Para obtener el complemento aparece, consulte [https://aka.ms/readyforwindows](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Utilice el Monitor de proceso para ayudar a depurar problemas de carga o de instalación
Si el complemento tiene problemas de compatibilidad durante la instalación o la carga, pueden estar relacionados con problemas de acceso de archivo o del registro. Use [Monitor de procesos](/sysinternals/downloads/procmon) u otra herramienta de depuración similar para iniciar sesión y comparar el comportamiento en un entorno de trabajo para ayudar a identificar el problema.
