---
title: "Consideraciones especiales para instalar Visual Studio en un entorno sin conexión | Microsoft Docs"
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 08/14/2017
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
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 62fc2d38a628cfc28913a0a45e1e3cb5d3852330
ms.contentlocale: es-es
ms.lasthandoff: 08/14/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Consideraciones especiales para instalar Visual Studio en un entorno sin conexión

Visual Studio está diseñado principalmente para su instalación desde una máquina conectada a Internet, dado que muchos componentes se actualizan periódicamente. Sin embargo, con algunos pasos adicionales, es posible implementar Visual Studio en un entorno donde no se encuentre disponible una conexión a Internet en funcionamiento.

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Instalación de los certificados necesarios para la instalación sin conexión de Visual Studio
El motor de instalación de Visual Studio solo instala el contenido que sea de confianza. Para ello, comprueba las firmas Authenticode del contenido que se descarga y confirma que todo el contenido es de confianza antes de instalarlo. Esto conserva su entorno seguro de los ataques donde la ubicación de descarga está en peligro. Por lo tanto, la instalación de Visual Studio necesita que varios certificados estándar intermedios y de raíz de Microsoft estén instalados y actualizados en un equipo de usuario. Si el equipo se mantiene actualizado con Windows Update, los certificados de firma se actualizan automáticamente, y durante la instalación de Visual Studio se actualizan los certificados si es necesario para comprobar las firmas de archivo.

Para las empresas con equipos sin conexión que no tienen los últimos certificados raíz, un administrador puede usar las instrucciones de la página [Configurar raíces de confianza y certificados no permitidos](https://technet.microsoft.com/en-us/library/dn265983.aspx) para actualizarlos. De manera alternativa, cuando crea un diseño de red, los certificados necesarios se descargan en la carpeta `certificates`. Después, puede instalar manualmente los certificados haciendo doble clic en el archivo de certificado y recorriendo el asistente del Administrador de certificados. Si se le solicita una contraseña, déjela en blanco.

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
Los tres archivos `.p12` de esta carpeta contienen un certificado intermedio y un certificado raíz. La mayoría de los sistemas que están actualizados con Windows Update tienen estos certificados ya instalados.

* `ManifestSignCertificates.p12` contiene:
    * Certificado intermedio: **Firma de código de Microsoft PCA 2011**
        * No es necesario. Mejora el rendimiento en algunos escenarios si está presente.
    * Certificado raíz: **Entidad de certificación raíz de Microsoft de 2011**
        * Necesario en sistemas de Windows 7 Service Pack 1 que no tienen las últimas actualizaciones de Windows instaladas.
* `ManifestCounterSignCertificates.p12`
    * Certificado intermedio: **Marca de tiempo de Microsoft PCA 2010**
        * No es necesario. Mejora el rendimiento en algunos escenarios si está presente.
    * Certificado raíz: **Entidad de certificación raíz de Microsoft de 2010**
        * Necesario en sistemas de Windows 7 Service Pack 1 que no tienen las últimas actualizaciones de Windows instaladas.
* `vs_installer_opc.SignCertificates.p12`
    * Certificado intermedio: **Firma de código de Microsoft PCA**
        * Necesario en todos los sistemas. Tenga en cuenta que los sistemas con todas las actualizaciones aplicadas de Windows Update puede que no tengan este certificado.
    * Certificado raíz: **Entidad de certificación raíz de Microsoft**
        * Obligatorio. Este certificado se proporciona con sistemas que ejecutan Windows 7 o versiones posteriores.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>¿Por qué los certificados de la carpeta `certificates` no se instalan automáticamente?
Cuando se comprueba una firma en un entorno en línea, se usan las API de Windows para descargar y agregar los certificados al sistema. Durante este proceso tiene lugar la comprobación de que el certificado es de confianza y que se permite mediante la configuración administrativa. Este proceso de comprobación no se puede producir en la mayoría de entornos sin conexión. Instalar los certificados manualmente permite a los administradores de empresa garantizar que los certificados son de confianza y que cumplen la directiva de seguridad de su organización.

### <a name="checking-if-certificates-are-already-installed"></a>Comprobar si los certificados ya están instalados
Una manera de comprobar el sistema de instalación es seguir estos pasos:
1. Ejecute `mmc.exe`.<br/>
  a. Haga clic en Archivo y, después, seleccione **Agregar o quitar complemento**.<br/>
  b. Haga doble clic en **Certificados**, seleccione **Cuenta de equipo** y, después, haga clic en **Siguiente**.<br/>
  c. Seleccione **Equipo local**, haga clic en **Finalizar** y, después, en **Aceptar**.<br/>
  d. Expanda **Certificados (equipo local)**.<br/>
  e. Expanda **Entidades de certificación raíz de confianza** y, después, seleccione **Certificados**.<br/>
    * Compruebe esta lista para ver los certificados raíz necesarios.<br/>
  
   f. Expanda **Entidades de certificación intermedias** y, después, seleccione **Certificados**.<br/>
    * Compruebe esta lista para ver los certificados intermedios necesarios.<br/>

2. Haga clic en Archivo y seleccione **Agregar o quitar complemento**.<br/>
  a. Haga doble clic en **Certificados**, seleccione **Mi cuenta de usuario**, haga clic en **Finalizar** y, después, en **Aceptar**.<br/>
  b. Expanda **Certificados: usuario actual**.<br/>
  c. Expanda **Entidades de certificación intermedias** y, después, seleccione **Certificados**.<br/>
    * Compruebe esta lista para ver los certificados intermedios necesarios.<br/>

Si los nombres de los certificados no estaban en las columnas **Emitido para**, deben instalarse.  Si un certificado intermedio solo estaba en el almacén de certificados intermedios del **usuario actual**, entonces solo está disponible para el usuario que ha iniciado sesión y puede que necesite instalarlo para otros usuarios.

## <a name="install-visual-studio"></a>Instalar Visual Studio
Después de instalar los certificados, la implementación de Visual Studio puede continuar sin conexión sin realizar pasos especiales adicionales siguiendo las instrucciones de la sección [Implementación de una instalación de red]((create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) de la página "Creación de una instalación de red de Visual Studio".


## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)

