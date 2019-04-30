---
title: Modificación del Shell aislado mediante el uso de la. Archivo Pkgundef | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538399"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modificación del Shell aislado mediante el uso de la. Archivo Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede modificar el archivo .pkgundef para excluir las entradas del registro especificado de una aplicación de shell aislado. Normalmente, la primera vez que se inicia una aplicación en un equipo, el shell de Visual Studio copia las entradas del registro de Visual Studio existentes a la clave del registro raíz para la aplicación. Esto incluye todas las referencias a VSPackages instalados actualmente.  
  
 Para excluir una entrada del Registro específica de una aplicación de shell aislado, agregue el archivo .pkgundef la aplicación la clave de paquete seguida de la entrada. Se representan las claves y entradas al igual que en el archivo .pkgdef; es decir, como [$RootKey$] o [$RootKey$\\*subclave*] y "*entrada*" =*valor*, donde *subclave* es la subclave para afectar, *entrada* es la entrada para quitar, y *valor* sea `""` o `dword:00000000`.  
  
 Para excluir varias entradas de una clave del registro, se trata de enumerar la clave de una vez, seguido de una línea para cada entrada que se excluirán.  
  
 Para excluir una clave del registro completo de una aplicación de shell aislado, agregue la clave en el archivo .pkgundef de aplicación pero no especifica ninguna entrada del registro para esa clave.  
  
 Puede agregar comentarios en el archivo .pkgundef. Una sola línea de comentario debe tener dos barras diagonales como los dos primeros caracteres.  
  
 Por ejemplo, para quitar el **conectar con base de datos** y **conectarse a r Server** comandos en el **herramientas** menú, puede quitar el comentario de la línea:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 y agregue la línea:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 en el archivo .pkgundef de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [GUID del paquete de características de Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalización del Shell aislado](../extensibility/customizing-the-isolated-shell.md)
