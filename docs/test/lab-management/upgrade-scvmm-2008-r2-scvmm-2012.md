---
title: Actualizar SCVMM 2008 R2 a SCVMM 2012 | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 51d907dfe25d8f27065b2a4d8bbecaa3e98e42a1
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>Actualizar SCVMM 2008 R2 a SCVMM 2012

Lab Management para Team Foundation Server admite SCVMM 2008 R2 y SCVMM 2012. Si va a actualizar Team Foundation Server 2013 a Team Foundation Server 2015 y piensa actualizar SCVMM 2008 R2 a SCVMM 2012, se recomienda hacer la actualización a SCVMM 2012 después de completar la actualización a Team Foundation Server 2015. En este tema se describe cómo actualizar SCVMM 2008 R2 a SCVMM 2012 cuando se está usando Lab Management en Team Foundation Server 2015.
Lab Management **no** admite SCVMM 2016. 

**Importante:** Al actualizar SCVMM, algunos pasos causarán cierto tiempo de inactividad para Team Foundation Server. Encontrará estos pasos a continuación.

## <a name="upgrading-to-scvmm-2012"></a>Actualizar a SCVMM 2012

1. Utilice el instalador de SCVMM 2012 para actualizar SCVMM 2008 R2 Server a SCVMM 2012 Server.

1. Actualice los agentes SCVMM en los hosts y en los recursos compartidos de biblioteca.

1. Utilice la consola de administración de SCVMM para comprobar que todos los componentes de SCVMM funcionan.

1. Instale la Consola de administración de SCVMM 2012 en todos los equipos de la capa de aplicación de Team Foundation Server.

1. Use el comando **iisreset** para reiniciar el servicio Web de Team Foundation Server. A continuación, reinicie el agente de trabajo de Team Foundation Server.

   **Precaución:** Este paso interrumpirá los servicios en Team Foundation Server.

1. Actualice los datos y las plantillas en todas las bases de datos de la colección de proyectos para que sean compatibles con SCVMM 
   2012.

   Abra un símbolo del sistema con privilegios elevados en Team Foundation Server y escriba el siguiente comando:

   **C:\\Program Files\\Microsoft Team Foundation Server 14.0\\Tools\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   Al usar el comando **upgradeSCVMM**, Team Foundation Server creará un nuevo objeto de plantilla en el servidor SCVMM para cada proyecto de equipo que use esa plantilla. Esto garantiza que las plantillas se actualizan para que sean compatibles con SCVMM 2012 sin perder ningún dato. Sin embargo, cuando se crean las nuevas plantillas, el nombre del proyecto de equipo se anexa al nombre de la plantilla.

   **Advertencia:**  
   Si el nombre de la nueva plantilla tiene más de 64 caracteres, se producirá un error de SCVMM. Para resolver este error, debe asignar a las plantillas un nombre más corto. Si aparecen otros errores o advertencias al ejecutar este comando, vea la próxima sección para resolver esos errores. Si no se produce ningún error o advertencia, la actualización se ha completado y puede empezar a utilizar entornos de SCVMM con Lab Management.

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>Resolver errores y advertencias al utilizar el comando upgradeSCVMM

Después de usar el comando **upgradeSCVMM**, debe resolver los errores o advertencias recibidas y volver a ejecutar el comando antes de empezar a usar Lab Management. El comando **upgradeSCVMM** genera un archivo de registro que contiene información sobre los errores y advertencias que encuentra. La ubicación del archivo de registro se muestra cuando se ejecuta el comando **upgradeSCVMM**.

**Error de SCVMM:** si recibe un error relacionado con un error de SCVMM, use el historial de trabajos SCVMM para obtener información adicional sobre el error. Después de resolver el error de SCVMM, vuelva a ejecutar el comando **upgradeSCVMM**.

## <a name="see-also"></a>Vea también

* [Cambiar las configuraciones de Lab Management existentes](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
