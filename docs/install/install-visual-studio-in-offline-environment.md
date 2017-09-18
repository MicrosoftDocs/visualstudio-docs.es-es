---
title: "Consideraciones especiales para instalar Visual Studio en un entorno sin conexión | Microsoft Docs"
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 06/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 1ce2f854d1c8e4a184446fb07c66a6fad9ca9ae1
ms.contentlocale: es-es
ms.lasthandoff: 06/23/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Consideraciones especiales para instalar Visual Studio en un entorno sin conexión

Visual Studio está diseñado principalmente para la instalación desde una máquina conectada a Internet, dado que muchos componentes se actualizan periódicamente. Sin embargo, con algunos pasos adicionales, es posible implementar Visual Studio en un entorno donde no se encuentre disponible una conexión a Internet en funcionamiento.

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Instalación de los certificados necesarios para la instalación sin conexión de Visual Studio
El motor de instalación de Visual Studio solo instalará el contenido que sea de confianza. Para ello, comprueba las firmas Authenticode del contenido que se descarga y confirma que todo el contenido es de confianza antes de instalarlo. Esto conserva su entorno seguro de los ataques donde la ubicación de descarga está en peligro. Por lo tanto, la instalación de Visual Studio necesita que varios certificados estándar intermedios y de raíz de Microsoft estén instalados y actualizados en un equipo de usuario. Si el equipo se mantiene actualizado con Windows Update, los certificados de firma se actualizan automáticamente, y durante la instalación de Visual Studio se actualizarán los certificados si es necesario para comprobar las firmas de archivo. 

Para las empresas con equipos sin conexión que no tienen los últimos certificados raíz, un administrador puede usar estas [instrucciones](https://technet.microsoft.com/en-us/library/dn265983.aspx) para actualizarlos. De manera alternativa, los certificados necesarios se descargan durante la creación de un diseño de red en la carpeta `certificates` y pueden instalarse manualmente haciendo doble clic en el archivo de certificado y, después, haciendo clic a través del Asistente del administrador de certificados. Si se le solicita una contraseña, déjela en blanco.

Si está creando el script de la implementación de Visual Studio en un entorno sin conexión en las áreas de trabajo del cliente, debe seguir estos pasos:

1. Copie la [herramienta del Administrador de certificados](https://msdn.microsoft.com/en-us/library/e78byta0.aspx) (`certmgr.exe`) en el recurso compartido de la instalación (por ejemplo, `\\server\share\vs2017`). `certmgr.exe` no está incluido como parte de Windows, pero está disponible como parte de [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk). 

2. Cree un archivo por lotes con los siguientes comandos:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   
   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   
   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Implemente el archivo por lotes en el cliente. Este comando debe ejecutarse desde un proceso elevado.

### <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>¿Cuáles son los archivos de certificado de la carpeta `certificates`?
Los tres archivos `.p12` de esta carpeta contienen un certificado intermedio y un certificado raíz. La mayoría de los sistema que están actualizados con Windows Update tendrán estos certificados ya instalados.

1. `ManifestSignCertificates.p12` contiene:
    * Certificado intermedio: **Firma de código de Microsoft PCA 2011**
        * No es necesario. Mejora el rendimiento en algunos escenarios si está presente.
    * Certificado raíz: **Entidad de certificación raíz de Microsoft de 2011**
        * Necesario en sistemas de Windows 7 Service Pack 1 que no tienen las últimas actualizaciones de Windows instaladas.
2. `ManifestCounterSignCertificates.p12`
    * Certificado intermedio: **Marca de tiempo de Microsoft PCA 2010**
        * No es necesario. Mejora el rendimiento en algunos escenarios si está presente.
    * Certificado raíz: **Entidad de certificación raíz de Microsoft de 2010**
        * Necesario en sistemas de Windows 7 Service Pack 1 que no tienen las últimas actualizaciones de Windows instaladas.
3. `vs_installer_opc.SignCertificates.p12`
    * Certificado intermedio: **Firma de código de Microsoft PCA**
        * Necesario en todos los sistemas. Tenga en cuenta que los sistemas con todas las actualizaciones aplicadas de Windows Update puede que no tengan este certificado.
    * Certificado raíz: **Entidad de certificación raíz de Microsoft**
        * Obligatorio. Este certificado se proporciona con sistemas que ejecutan Windows 7 o versiones posteriores.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>¿Por qué los certificados de la carpeta `certificates` no se instalan automáticamente?
Cuando se comprueba una firma en un entorno en línea, se usan las API de Windows para descargar y agregar los certificados al sistema. Durante este proceso tiene lugar la comprobación de que el certificado es de confianza y que se permite mediante la configuración administrativa. Este proceso de comprobación no se puede producir en la mayoría de entornos sin conexión. Instalar los certificados manualmente permite a los administradores de empresa garantizar que los certificados son de confianza y que cumplen la directiva de seguridad de su organización.

### <a name="checking-if-certificates-are-already-installed"></a>Comprobar si los certificados ya están instalados
Una manera de comprobar el sistema de instalación es seguir estos pasos:
* Ejecute mmc.exe
* Haga clic en Archivo y seleccione Agregar o quitar complemento
  * Haga doble clic en **Certificados**, seleccione **Cuenta de equipo** y haga clic en **Siguiente**
  * Seleccione **Equipo local**, haga clic en **Finalizar** y en **Aceptar**
  * Expanda **Certificados (equipo local)**
  * Expanda **Entidades de certificación raíz de confianza** y seleccione **Certificados**
    * Compruebe esta lista para ver los certificados raíz necesarios.
  * Expanda **Entidades de certificación intermedias** y seleccione **Certificados**
    * Compruebe esta lista para ver los certificados intermedios necesarios.
* Haga clic en Archivo y seleccione Agregar o quitar complemento
  * Haga doble clic en **Certificados**, seleccione **Mi cuenta de usuario**, haga clic en **Finalizar** y **Aceptar**.
  * Expanda **Certificados: usuario actual**
  * Expanda **Entidades de certificación intermedias** y seleccione **Certificados**
    * Compruebe esta lista para ver los certificados intermedios necesarios.
    
Si los nombres de los certificados no estaban en las columnas **Emitido para**, necesitarán instalarse.  Si un certificado intermedio solo estaba en el almacén de certificados intermedios del **usuario actual**, entonces solo está disponible para el usuario que ha iniciado sesión y puede que necesite instalarse para otros usuarios.

## <a name="install-visual-studio"></a>Instalar Visual Studio
Después de haber instalado los certificados, la implementación de Visual Studio puede continuar sin conexión sin necesidad de pasos adicionales especiales; basta con seguir [estas instrucciones](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation).


## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)

