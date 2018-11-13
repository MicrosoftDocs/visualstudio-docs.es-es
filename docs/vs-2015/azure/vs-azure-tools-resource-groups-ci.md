---
title: Integración continua en Azure DevOps Services mediante proyectos del grupo de recursos de Azure | Microsoft Docs
description: Describe cómo configurar la integración continua en Azure DevOps Services mediante proyectos de implementación de grupo de recursos de Azure en Visual Studio.
author: mlearned
manager: douge
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.service: azure-resource-manager
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: f6404b15e8a7cd3f95ac63bbae6076ef62fcff06
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003006"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Integración continua en Azure DevOps Services mediante proyectos de implementación de grupo de recursos de Azure
Para implementar una plantilla de Azure, realizar tareas en varias fases: compilación, prueba, copia en Azure (también denominado "Ensayo") y plantilla de implementación. Hay dos maneras diferentes para implementar plantillas en servicios de Azure DevOps. Ambos métodos proporcionan los mismos resultados, así que elija aquella que mejor se adapte a su flujo de trabajo.

1. Agregue un paso único a la canalización de compilación que se ejecuta el script de PowerShell que se incluye en el proyecto de implementación de grupo de recursos de Azure (Deploy-AzureResourceGroup.ps1). El script copia los artefactos y, a continuación, implementa la plantilla.
2. Agregar que varios servicios de Azure DevOps pasos de compilación, cada uno de ellos realiza una tarea de fase.

En este artículo se muestra ambas opciones. La primera opción tiene la ventaja de usar la misma secuencia de comandos usado por los desarrolladores en Visual Studio y proporcionar coherencia en todo el ciclo de vida. La segunda opción ofrece una alternativa conveniente al script integrado. Ambos procedimientos suponen que ya tiene un proyecto de implementación de Visual Studio activado en servicios de Azure DevOps.

## <a name="copy-artifacts-to-azure"></a>Copie los artefactos en Azure
Independientemente del escenario, si dispone de los artefactos que son necesarios para la implementación de plantilla, debe dar acceso a Azure Resource Manager para ellos. Estos artefactos pueden incluir archivos, como:

* Plantillas anidadas
* Los scripts de configuración y los scripts de DSC
* Archivos binarios de aplicación

### <a name="nested-templates-and-configuration-scripts"></a>Las plantillas anidadas y Scripts de configuración
Al utilizar las plantillas proporcionadas por Visual Studio (o compilar con fragmentos de código de Visual Studio), el script de PowerShell no solo almacena provisionalmente los artefactos, sino que parametriza también el URI de los recursos de las distintas implementaciones. El script copia los artefactos en un contenedor seguro en Azure, crea un token de SaS de dicho contenedor y, a continuación, pasa esta información a la implementación de plantilla. Consulte [crear una implementación de plantilla](https://msdn.microsoft.com/library/azure/dn790564.aspx) para obtener más información sobre las plantillas anidadas.  Cuando se usan tareas en los servicios de Azure DevOps, debe seleccionar las tareas adecuadas para la implementación de plantilla y si es necesario, pasar valores de parámetro en el paso de almacenamiento provisional para la implementación de plantilla.

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>Configurar implementación continua en las canalizaciones de Azure
Para llamar a la secuencia de comandos de PowerShell en las canalizaciones de Azure, deberá actualizar la canalización de compilación. En resumen, los pasos son: 

1. Editar la canalización de compilación.
2. Configurar la autorización de Azure en las canalizaciones de Azure.
3. Agregue un paso de compilación de Azure PowerShell que hace referencia a la secuencia de comandos de PowerShell en el proyecto de implementación de grupo de recursos de Azure.
4. Establezca el valor de la *- ArtifactsStagingDirectory* parámetro para trabajar con un proyecto compilado en las canalizaciones de Azure.

### <a name="detailed-walkthrough-for-option-1"></a>Tutorial detallado para la opción 1
Los procedimientos siguientes le guiarán a través de los pasos necesarios para configurar la implementación continua en servicios de Azure DevOps con una sola tarea que ejecuta el script de PowerShell en el proyecto. 

1. Edite la canalización de compilación de servicios de DevOps de Azure y agregue un paso de compilación de Azure PowerShell. Elija la canalización de compilación bajo la **crear canalizaciones** categoría y, a continuación, elija el **editar** vínculo.
   
   ![Editar la canalización de compilación][0]
2. Agregue un nuevo **Azure PowerShell** paso a la canalización de compilación de compilación y, a continuación, elija el **Agregar paso de compilación...** .
   
   ![Agregar paso de compilación][1]
3. Elija la **tarea de implementación** categoría, seleccione el **Azure PowerShell** de tareas y, a continuación, elija su **agregar** botón.
   
   ![Agregar tareas][2]
4. Elija la **Azure PowerShell** paso de compilación y, a continuación, rellene sus valores.
   
   1. Si ya tiene un punto de conexión de servicio de Azure agregado a los servicios de Azure DevOps, elija la suscripción en el **suscripción Azure** cuadro de lista desplegable y, a continuación, vaya directamente a la sección siguiente. 
      
      Si no tiene un punto de conexión de servicio de Azure en los servicios de Azure DevOps, deberá agregar uno. Este subapartado le guiará por el proceso. Si su cuenta de Azure usa una cuenta de Microsoft (como Hotmail), debe realizar los pasos siguientes para obtener una autenticación de entidad de servicio.

   2. Elija la **administrar** vínculo junto a la **suscripción Azure** cuadro de lista desplegable.
      
      ![Administrar suscripciones de Azure][3]
   3. Elija **Azure** en el **nuevo extremo de servicio** cuadro de lista desplegable.
      
      ![Nuevo punto de conexión de servicio][4]
   4. En el **Agregar suscripción de Azure** cuadro de diálogo, seleccione el **Serviceprincipal** opción.
      
      ![Opción de entidad de servicio][5]
   5. Agregue la información de suscripción de Azure para la **Agregar suscripción de Azure** cuadro de diálogo. Deberá proporcionar los siguientes elementos:
      
      * Id. de suscripción
      * Nombre de la suscripción
      * Id. de entidad de servicio
      * Clave de entidad de servicio
      * Id. de inquilino
   6. Agregar un nombre de su elección para el **suscripción** cuadro Nombre. Este valor aparecerá más adelante en el **suscripción Azure** lista desplegable en los servicios de Azure DevOps. 

   7. Si no conoce el identificador de suscripción de Azure, puede usar uno de los siguientes comandos para recuperarlo.
      
      Para los scripts de PowerShell, use:
      
      `Get-AzureRmSubscription`
      
      CLI de Azure, use:
      
      `azure account show`
   8. Para obtener un Id. de entidad de servicio, clave de entidad de servicio y el identificador de inquilino, siga el procedimiento de [aplicación crear Active Directory y entidad de servicio mediante el portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal) o [autenticar una entidad de servicio con Azure El Administrador de recursos](/azure/azure-resource-manager/resource-group-authenticate-service-principal).
   9. Agregue los valores de Id. de entidad de servicio, la clave de entidad de servicio y el identificador del inquilino a la **Agregar suscripción de Azure** diálogo cuadro y, a continuación, elija el **Aceptar** botón.
      
      Ahora dispone de una entidad de servicio válido se utiliza para ejecutar el script de PowerShell de Azure.
5. Edite la canalización de compilación y elija el **Azure PowerShell** paso de compilación. Seleccione la suscripción en el **suscripción Azure** cuadro de lista desplegable. (Si la suscripción no aparece, elija el **actualizar** aparece al lado del **administrar** vínculo.) 
   
   ![Configurar la tarea de compilación de Azure PowerShell][8]
6. Proporcione una ruta de acceso al script de PowerShell Deploy-AzureResourceGroup.ps1. Para ello, elija el botón de puntos suspensivos (...) junto a la **ruta del Script** , navegue hasta la secuencia de comandos de PowerShell Deploy-AzureResourceGroup.ps1 en el **Scripts** carpeta del proyecto, seleccione y, a continuación, Elija la **Aceptar** botón.    
   
   ![Seleccione la ruta de acceso a la secuencia de comandos][9]
7. Después de seleccionar el script, actualice la ruta de acceso a la secuencia de comandos para que se ejecuta desde el Build.StagingDirectory (el mismo directorio que *ArtifactsLocation* está establecido en). Puede hacerlo agregando "$(Build.stagingdirectory) /"al principio de la ruta de acceso del script.
   
    ![Editar ruta de acceso a la secuencia de comandos][10]
8. En el **argumentos del Script** , escriba los parámetros siguientes (en una sola línea). Al ejecutar el script en Visual Studio, puede ver cómo usa VS los parámetros en el **salida** ventana. Puede usar como punto de partida para configurar los valores de parámetro en el paso de compilación.
   
   | Parámetro | Descripción |
   | --- | --- |
   | -ResourceGroupLocation |El valor de ubicación geográfica donde se encuentra, como el grupo de recursos **eastus** o **'East US'**. (Agregue comillas simples si hay un espacio en el nombre). Consulte [regiones de Azure](https://azure.microsoft.com/regions/) para obtener más información. |
   | -ResourceGroupName |El nombre del grupo de recursos utilizado para esta implementación. |
   | -UploadArtifacts |Este parámetro, cuando está presente, especifica que los artefactos tienen que cargarse en Azure desde el sistema local. Solo debe establecer este modificador si su implementación de plantilla requiere artefactos adicionales que desea almacenar provisionalmente mediante el script de PowerShell (por ejemplo, los scripts de configuración o plantillas anidadas). |
   | -StorageAccountName |El nombre de la cuenta de almacenamiento utilizada para almacenar provisionalmente los artefactos para esta implementación. Este parámetro solo se usa si almacena provisionalmente los artefactos para la implementación. Si se proporciona este parámetro, se crea una nueva cuenta de almacenamiento si no ha creado la secuencia de comandos durante una implementación anterior. Si se especifica el parámetro, ya debe existir la cuenta de almacenamiento. |
   | -StorageAccountResourceGroupName |El nombre del grupo de recursos asociado con la cuenta de almacenamiento. Este parámetro es necesario sólo si proporciona un valor para el parámetro StorageAccountName. |
   | -TemplateFile |La ruta de acceso al archivo de plantilla en el proyecto de implementación de grupo de recursos de Azure. Para mejorar la flexibilidad, utilice una ruta de acceso para este parámetro que sea relativa a la ubicación del script de PowerShell en lugar de una ruta de acceso absoluta. |
   | -TemplateParametersFile |La ruta de acceso al archivo de parámetros en el proyecto de implementación de grupo de recursos de Azure. Para mejorar la flexibilidad, utilice una ruta de acceso para este parámetro que sea relativa a la ubicación del script de PowerShell en lugar de una ruta de acceso absoluta. |
   | -ArtifactStagingDirectory |Este parámetro permite que el script de PowerShell conozca la carpeta desde donde se deben copiar los archivos binarios del proyecto. Este valor invalida el valor predeterminado utilizado por el script de PowerShell. Para usar servicios de Azure DevOps, establezca el valor en: ArtifactStagingDirectory-$ (Build.stagingdirectory) |
   
   Este es un ejemplo de argumentos de script (línea dividida para mejorar la legibilidad):
   
   ```    
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json' 
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct' 
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'    
   ```
   
   Cuando haya terminado, la **argumentos del Script** cuadro debería parecerse a la lista siguiente:
   
   ![Argumentos de script][11]
9. Después de agregar todos los elementos necesarios para el paso de compilación de Azure PowerShell, elija el **cola** botón para generar el proyecto de compilación. El **compilar** pantalla muestra la salida del script de PowerShell.

### <a name="detailed-walkthrough-for-option-2"></a>Tutorial detallado para la opción 2
Los procedimientos siguientes le guiarán a través de los pasos necesarios para configurar la implementación continua en servicios de Azure DevOps con las tareas integradas.

1. Editar la canalización de compilación de servicios de Azure DevOps para agregar que dos nuevos pasos de compilación. Elija la canalización de compilación bajo la **las definiciones de compilación** categoría y, a continuación, elija el **editar** vínculo.
   
   ![Editar definición de compilación][12]
2. Agregar los nuevos pasos de compilación a la canalización de compilación con el **Agregar paso de compilación...** .
   
   ![Agregar paso de compilación][13]
3. Elija la **implementar** categoría de tarea, seleccione el **Azure File Copy** de tareas y, a continuación, elija su **agregar** botón.
   
   ![Agregar tarea copia de archivos de Azure][14]
4. Elija la **implementación del grupo de recursos de Azure** de tareas y, después, elija su **agregar** botón y, a continuación, **cerrar** el **catálogo de tareas**.
   
   ![Agregar tarea de implementación de grupo de recursos de Azure][15]
5. Elija la **Azure File Copy** de tareas y rellene sus valores.
   
   Si ya tiene un punto de conexión de servicio de Azure agregado a los servicios de Azure DevOps, elija la suscripción en el **suscripción Azure** cuadro de lista desplegable. Si no tiene una suscripción, consulte [Option 1](#detailed-walkthrough-for-option-1) para obtener instrucciones sobre cómo configurar uno en servicios de Azure DevOps.
   
   * Origen: escriba **$ (Build.stagingdirectory)**
   * Tipo de conexión de Azure: seleccione **Azure Resource Manager**
   * Suscripción de Azure RM: seleccione la suscripción para la cuenta de almacenamiento que desea usar en el **suscripción Azure** cuadro de lista desplegable. Si la suscripción no aparece, elija el **actualizar** aparece al lado del **administrar** vínculo.
   * Tipo de destino: seleccione **blobs de Azure**
   * RM cuenta de almacenamiento: seleccione la cuenta de almacenamiento desea usar para almacenar artefactos provisionalmente
   * Nombre de contenedor: escriba el nombre del contenedor que le gustaría usar para el almacenamiento provisional; puede ser cualquier nombre de contenedor válido, pero uno dedicado a esta canalización de compilación
   
   Para los valores de salida:
   
   * Escriba el contenedor de almacenamiento de URI - **artifactsLocation**
   * Token SAS del contenedor de almacenamiento: escriba **artifactsLocationSasToken**
   
   ![Configurar la tarea copia de archivos de Azure][16]
6. Elija la **implementación del grupo de recursos de Azure** paso de compilación y, a continuación, rellene sus valores.
   
   * Tipo de conexión de Azure: seleccione **Azure Resource Manager**
   * Suscripción de Azure RM: seleccione la suscripción para su implementación en el **suscripción Azure** cuadro de lista desplegable. Esto suele ser la misma suscripción utilizada en el paso anterior
   * Acción: seleccione **crear o actualizar grupo de recursos**
   * Grupo de recursos: seleccione un grupo de recursos o escriba el nombre de un grupo de recursos para la implementación
   * Ubicación: seleccione la ubicación del grupo de recursos
   * Plantilla: escriba la ruta de acceso y el nombre de la plantilla que se implementarán anteponiendo **$ (Build.stagingdirectory)**, por ejemplo: **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * Parámetros de plantilla: escriba la ruta de acceso y el nombre de los parámetros que se usará, anteponiendo **$ (Build.stagingdirectory)**, por ejemplo: **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * Reemplazar parámetros de plantilla: escriba o copie y pegue el código siguiente:
     
     ```    
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```
     ![Configurar la tarea de implementación de grupo de recursos de Azure][17]
7. Después de agregar todos los elementos necesarios, guarde la canalización de compilación y elija **poner nueva compilación en cola** en la parte superior.

## <a name="next-steps"></a>Pasos siguientes
Lectura [Introducción a Azure Resource Manager](/azure-resource-manager/resource-group-overview.md) para obtener más información sobre Azure Resource Manager y grupos de recursos de Azure.

[0]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png
[1]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png
[2]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png
[3]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png
[4]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png
[5]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png
[8]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png
[9]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png
[10]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png
[11]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png
[12]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png
[13]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png
[14]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png
[15]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png
[16]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png
[17]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png
