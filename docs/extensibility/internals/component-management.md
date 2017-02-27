---
title: "Administraci&#243;n de componentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instalación [Visual Studio SDK], componentes"
  - "instalación [Visual Studio SDK], administración de archivos"
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Administraci&#243;n de componentes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Unidades de tareas de Windows Installer se denominan componentes de Windows Installer \(a veces denominado WICs o solo los componentes\).  GUID identifica cada WIC, que es la unidad básica de instalación y de recuento de referencias para las configuraciones que utilizan Windows Installer.  
  
 Aunque puede utilizar varios productos para crear el instalador de VSPackage, esta explicación se presupone el uso de archivos de Windows Installer \(.msi\).  Al crear el instalador, debe para controlar correctamente la implementación del archivo para que suceda el recuento de referencias correcto siempre.  Por consiguiente, versiones diferentes del producto no interferirán con o se quiten en una combinación de instalación y no desinstalarán escenarios.  
  
 En Windows Installer, el recuento de referencias aparece en el nivel de componente.  Debe organizar minuciosamente los recursos \(archivos, entradas del Registro, etc.\) en los componentes.  Hay otros niveles de organización \(como módulos, características, y productos \)que pueden ayudar en escenarios diferentes.  Para obtener más información, vea [Fundamentos de Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## Las instrucciones de configuración de creación para la instalación en paralelo  
  
-   Cree los archivos y las claves del Registro que se comparten entre versiones en sus propios componentes.  
  
     Esto permite fácilmente los utiliza en la versión siguiente.  Por ejemplo, bibliotecas de tipos registrados global, extensiones de archivo, otros elementos registrado en HKEY\_CLASSES\_ROOT, etc.  
  
-   Agrupe los componentes compartidos en los módulos de combinación independientes.  
  
     Esto le ayuda a crear correctamente para en paralelo avanzando.  
  
-   Instale los archivos compartidos y las claves del Registro utilizando los mismos componentes de Windows Installer entre las versiones.  
  
     Si utiliza un componente diferente, se desinstalan los archivos y las entradas del Registro cuando se desinstala un VSPackage versión pero otro Paquete todavía está instalado.  
  
-   No mezcle los elementos con control de versiones y compartidos en el mismo componente.  
  
     Al hacerlo se impide instalar elementos compartidos en una ubicación global y elementos pertenecen a ubicaciones aisladas.  
  
-   No han compartido las claves del Registro que señalan a los archivos con control de versiones.  
  
     Si lo hace, claves compartidas se sobrescritas cuando otro paquete VSPackage versión está instalado.  Después de quitar se va la segunda versión, el archivo al que la clave está informando.  
  
## Vea también  
 [Elegir entre VSPackages compartido y su versión](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Escenarios de instalación de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)