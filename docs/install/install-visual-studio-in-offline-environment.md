---
title: "Consideraciones especiales para instalar Visual Studio en un entorno sin conexión | Microsoft Docs"
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 05/09/2017
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Consideraciones especiales para instalar Visual Studio en un entorno sin conexión

Visual Studio está diseñado principalmente para la instalación desde una máquina conectada a Internet, dado que muchos componentes se actualizan periódicamente. Sin embargo, con algunos pasos adicionales, es posible implementar Visual Studio en un entorno donde no se encuentre disponible una conexión a Internet en funcionamiento.

## <a name="create-a-network-installation-layout"></a>Creación de un diseño de instalación de red
* Para más información, consulte [Create a network-based installation of Visual Studio](create-a-network-installation-of-visual-studio.md) (Creación de una instalación basada en red de Visual Studio).

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Instalación de los certificados necesarios para la instalación sin conexión de Visual Studio
El motor de instalación de Visual Studio solo instalará el contenido que sea de confianza.  Para ello, comprueba las firmas Authenticode del contenido que se descarga y confirma que es de confianza antes de instalarlo.  Las máquinas con acceso a Internet descargan e instalan automáticamente los certificados necesarios para comprobar las firmas de archivo.  Sin embargo, si trabaja en un entorno sin conexión, o en un sistema con una conexión a Internet deficiente, puede que esto no sea posible.  Para los usuarios de ese entorno, debe asegurarse de que se hayan instalado previamente los certificados necesarios.  La máquina en ejecución descarga estos certificados en la carpeta "certificates" al crear una instalación sin conexión.

Puede instalar los certificados en el cliente manualmente; para ello, haga doble clic en el archivo de certificado y luego recorra el asistente del Administrador de certificados. Si se le solicita una contraseña, déjela en blanco.

Para generar el script de instalación de los certificados, siga estos pasos:

1. Copie certmgr.exe en el recurso compartido de instalación (por ejemplo, `\server\share\vs2017`). `certmgr.exe` se incluye con el SDK de Windows, que se puede instalar como un componente opcional en la carga de trabajo de _desarrollo de la Plataforma universal de Windows_. (por ejemplo: `"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`)

2. Cree un archivo por lotes con los siguientes comandos:

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. Ejecute el archivo por lotes en el cliente desde un shell de comandos de administrador o un proceso con privilegios elevados.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>¿Por qué los certificados de la carpeta `certificates` no se instalan automáticamente?
Cuando se comprueba una firma en un entorno en línea, se usan las API de Windows para descargar y agregar los certificados al sistema. Durante este proceso tiene lugar la comprobación de que el certificado es de confianza y que se permite mediante la configuración administrativa. Este proceso de comprobación no se puede producir en la mayoría de entornos sin conexión. La instalación manual de los certificados permite al usuario asegurarse de que los certificados son de confianza y cumplen los requisitos del administrador.

## <a name="install-visual-studio"></a>Instalar Visual Studio
Después de haber instalado los certificados, la implementación de Visual Studio puede continuar sin conexión sin necesidad de pasos adicionales especiales; basta con seguir [estas instrucciones](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation).


## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)

