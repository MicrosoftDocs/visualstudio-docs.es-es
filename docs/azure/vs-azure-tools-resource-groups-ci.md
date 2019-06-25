---
title: Integración continua de Azure DevOps Services con proyectos del grupo de recursos de Azure | Microsoft Docs
description: Describe cómo configurar la integración continua de Azure DevOps Services mediante proyectos de implementación del grupo de recursos de Azure en Visual Studio.
author: mlearned
manager: jillfra
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: 1d3904c488186dbbde326619420dd55e71c3af04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568917"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Integración continua de Azure DevOps Services con proyectos del grupo de recursos de Azure

Para implementar una plantilla de Azure, es necesario realizar tareas en varias fases: compilación, prueba, copia en Azure (también denominado "almacenamiento provisional") e implementación de plantilla. Hay dos maneras distintas de implementar plantillas en Azure DevOps Services. Ambos métodos proporcionan los mismos resultados, así que puede elegir el que mejor se adapte a su flujo de trabajo.

1. Agregue un paso único a la canalización de compilación que ejecuta el script de PowerShell incluido en el proyecto de implementación del grupo de recursos de Azure (Deploy-AzureResourceGroup.ps1). El script copia los artefactos y, a continuación, implementa la plantilla.
2. Agregue varios pasos de compilación de Azure DevOps Services, cada uno de los cuales realiza una tarea de fase.

En este artículo se muestran ambas opciones. La primera opción tiene la ventaja de usar el mismo script que usan los desarrolladores en Visual Studio y proporcionar coherencia en todo el ciclo de vida. La segunda opción ofrece una alternativa conveniente al script integrado. En ambos procedimientos se supone que ya tiene un proyecto de implementación de Visual Studio activado en Azure DevOps Services.

## <a name="copy-artifacts-to-azure"></a>Copia de artefactos en Azure
Independientemente del escenario, si dispone de los artefactos necesarios para la implementación de plantillas, debe dar a Azure Resource Manager acceso a ellos. Estos artefactos pueden incluir archivos como:

* Plantillas anidadas
* Scripts de configuración y de DSC
* Archivos binarios de aplicación

### <a name="nested-templates-and-configuration-scripts"></a>Plantillas anidadas y scripts de configuración
Al utilizar las plantillas proporcionadas por Visual Studio (o compilar con fragmentos de código de Visual Studio), el script de PowerShell no solo almacena provisionalmente los artefactos, sino que parametriza también el URI de los recursos de las distintas implementaciones. El script copia los artefactos en un contenedor seguro de Azure, crea un token de SaS para dicho contenedor y, a continuación, pasa esta información a la implementación de plantilla. Consulte [Crear una implementación de plantilla](https://msdn.microsoft.com/library/azure/dn790564.aspx) para obtener más información acerca de las plantillas anidadas.  Cuando se usan tareas en Azure DevOps Services, debe seleccionar las tareas adecuadas para la implementación de plantilla y, si es necesario, pasar valores de parámetro desde el paso de almacenamiento provisional a la implementación de plantilla.

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>Configuración de la implementación continua en Azure Pipelines
Para llamar al script de PowerShell en Azure Pipelines, debe actualizar la canalización de compilación. En resumen, los pasos son:

1. Edición de la canalización de compilación.
2. Configuración de la autorización de Azure en Azure Pipelines.
3. Incorporación de un paso de compilación de Azure PowerShell que hace referencia al script de PowerShell en el proyecto de implementación del Grupo de recursos de Azure.
4. Establecimiento del valor del parámetro *-ArtifactsStagingDirectory* para trabajar con un proyecto compilado en Azure Pipelines.

### <a name="detailed-walkthrough-for-option-1"></a>Tutorial detallado para la opción 1
Los procedimientos siguientes le guiarán a través de los pasos necesarios para configurar la implementación continua en Azure DevOps Services con una sola tarea que ejecuta el script de PowerShell en el proyecto.

1. Edite la canalización de compilación de Azure DevOps Services y agregue un paso de compilación de Azure PowerShell. Seleccione la canalización de compilación en la categoría **Canalizaciones de compilación** y luego elija el vínculo **Editar**.

   ![Edición de la canalización de compilación](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png)
2. Agregue un nuevo paso de compilación de **Azure PowerShell** a la canalización de compilación y elija el botón **Agregar paso de compilación...** .

   ![Incorporación de un paso "Compilar"](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png)
3. Elija la categoría de **tarea Implementar**, seleccione la tarea **Azure PowerShell** y, a continuación, elija el botón **Agregar** correspondiente.

   ![Adición de tareas](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png)
4. Elija el paso de compilación **Azure PowerShell** y rellene sus valores.

   1. Si ya tiene un punto de conexión de servicio de Azure agregado a Azure DevOps Services, elija la suscripción en el cuadro de lista desplegable **Suscripción de Azure** y vaya a la sección siguiente.

      Si no tiene ningún punto de conexión de servicio de Azure en Azure DevOps Services, debe agregar uno. Este subapartado le guiará por el proceso. Si su cuenta de Azure usa una cuenta de Microsoft (como Hotmail), debe seguir estos pasos para obtener una autenticación de entidad de servicio.

   2. Elija el vínculo **Administrar** situado junto al cuadro de lista desplegable **Suscripción de Azure**.

      ![Administración de suscripciones de Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png)
   3. Elija **Azure** en el cuadro de lista desplegable **Nuevo punto de conexión de servicio**.

      ![Nuevo punto de conexión de servicio](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png)
   4. En el cuadro de diálogo **Agregar suscripción de Azure**, seleccione la opción **Entidad de servicio**.

      ![Opción de entidad de servicio](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png)
   5. Agregue la información de suscripción de Azure en el cuadro de diálogo **Agregar suscripción de Azure** . Debe proporcionar los siguientes elementos:

      * Id. de suscripción
      * Subscription Name
      * Id. de entidad del servicio
      * Clave de entidad del servicio 
      * Identificador de inquilino
   6. Agregue un nombre de su elección en el cuadro de nombre **Suscripción** . Este valor aparecerá más adelante en la lista desplegable **Suscripción de Azure** en Azure DevOps Services.

   7. Si no conoce el identificador de la suscripción de Azure, puede usar uno de los siguientes comandos para recuperarlo.

      Para scripts de PowerShell, use:

      `Get-AzureRmSubscription`

      Para la CLI de Azure, utilice:

      `azure account show`
   8. Para obtener un id. de entidad de servicio, una clave de entidad de servicio y un id. de inquilino, siga el procedimiento de [Creación de aplicación de Active Directory y entidad de servicio mediante el portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal) o [Autenticación de una entidad de servicio con Azure Resource Manager](/azure/azure-resource-manager/resource-group-authenticate-service-principal).
   9. Agregue los valores del identificador de entidad de servicio, de la clave de entidad de servicio y del identificador de inquilino en el cuadro de diálogo **Agregar suscripción de Azure** y, después, elija el botón **Aceptar**.

      Ahora dispone de una entidad de servicio válida que puede utilizar para ejecutar el script de Azure PowerShell.
5. Edite la canalización de compilación y elija el paso de compilación **Azure PowerShell**. Seleccione la suscripción en el cuadro de lista desplegable **Suscripción de Azure**. (Si la suscripción no aparece, elija el botón **Actualizar** junto al vínculo **Administrar**).

   ![Configure la tarea de compilación de Azure PowerShell](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png)
6. Proporcione una ruta de acceso al script de PowerShell Deploy-AzureResourceGroup.ps1. Para ello, elija el botón de puntos suspensivos (...) junto al cuadro **Ruta de acceso del script**, vaya al script de PowerShell Deploy-AzureResourceGroup.ps1 en la carpeta **Scripts** del proyecto, selecciónelo y elija el botón **Aceptar**.

   ![Selección de ruta de acceso a script](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png)
7. Después de seleccionar el script, actualice la ruta de acceso al script para que se ejecute desde Build.StagingDirectory (el mismo directorio en el que está establecido *ArtifactsLocation* ). Puede hacerlo agregando “$(Build.StagingDirectory)/” al principio de la ruta de acceso del script.

    ![Edición de ruta de acceso a script](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png)
8. En el cuadro **Argumentos del script** escriba los parámetros siguientes (en una sola línea). Al ejecutar el script en Visual Studio, puede ver cómo usa VS los parámetros en la ventana **Resultados** . Se puede utilizar como punto de partida para configurar los valores de parámetro en el paso de compilación.

   | Parámetro | DESCRIPCIÓN |
   | --- | --- |
   | -ResourceGroupLocation |El valor de la ubicación geográfica donde se encuentra el grupo de recursos, como **eastus** o **'Este de EE. UU.'**. (Agregue comillas simples si hay un espacio en el nombre). Para más información, consulte [Regiones de Azure](https://azure.microsoft.com/regions/). |
   | -ResourceGroupName |El nombre del grupo de recursos que se usa para esta implementación. |
   | -UploadArtifacts |Este parámetro, cuando está presente, especifica que los artefactos tienen que cargarse en Azure desde el sistema local. Solo debe establecer este modificador si su implementación de plantilla requiere artefactos adicionales que desea almacenar provisionalmente mediante el script de PowerShell (como scripts de configuración o plantillas anidadas). |
   | -StorageAccountName |El nombre de la cuenta de almacenamiento utilizada para almacenar provisionalmente los artefactos en esta implementación. Este parámetro solo se usa si almacena provisionalmente los artefactos para la implementación. Si se suministra este parámetro se crea una cuenta de almacenamiento nueva si el script no creó ninguna durante una implementación anterior. Si se especifica el parámetro, ya debe existir la cuenta de almacenamiento. |
   | -StorageAccountResourceGroupName |El nombre del grupo de recursos asociado a la cuenta de almacenamiento. Este parámetro solo se requiere si se proporciona un valor para el parámetro StorageAccountName. |
   | -TemplateFile |La ruta de acceso al archivo de plantilla en el proyecto de implementación del Grupo de recursos de Azure. Para mejorar la flexibilidad, utilice una ruta de acceso para este parámetro que sea relativa a la ubicación del script de PowerShell en lugar de una ruta de acceso absoluta. |
   | -TemplateParametersFile |La ruta de acceso al archivo de parámetros en el proyecto de implementación del Grupo de recursos de Azure. Para mejorar la flexibilidad, utilice una ruta de acceso para este parámetro que sea relativa a la ubicación del script de PowerShell en lugar de una ruta de acceso absoluta. |
   | -ArtifactStagingDirectory |Este parámetro permite que el script de PowerShell conozca la carpeta desde la que se deben copiar los archivos binarios del proyecto. Este valor invalida el valor predeterminado usado por el script de PowerShell. Para el uso de Azure DevOps Services, establezca el valor en: -ArtifactStagingDirectory $(Build.StagingDirectory) |

   A continuación se muestra un ejemplo de argumentos de script (línea dividida para mejorar la legibilidad):

   ```
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json'
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct'
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'
   ```

   Cuando haya terminado, el cuadro **Argumentos del script** debe ser similar a la lista siguiente:

   ![Argumentos de script](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png)
9. Después de agregar todos los elementos necesarios para el paso de compilación de Azure PowerShell, elija el botón de compilación **Cola** para generar el proyecto de compilación. La pantalla **Compilación** muestra el resultado del script de PowerShell.

### <a name="detailed-walkthrough-for-option-2"></a>Tutorial detallado para la opción 2
Los procedimientos siguientes le guiarán por los pasos necesarios para configurar la implementación continua en Azure DevOps Services con las tareas integradas.

1. Edite la canalización de compilación de Azure DevOps Services para agregar que dos nuevos pasos de compilación. Seleccione la canalización de compilación en la categoría **Definiciones de compilación** y luego elija el vínculo **Editar**.

   ![Editar definición de compilación](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png)
2. Agregue los nuevos pasos de compilación a la canalización de compilación con el botón **Incorporación de un paso "Compilar"...** .

   ![Incorporación de un paso "Compilar"](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png)
3. Elija la categoría de tarea **Implementar**, seleccione la tarea **Copia de archivos de Azure** y, luego, haga clic en el botón **Agregar**.

   ![Incorporación de la tarea Copia de archivos de Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png)
4. Elija la tarea **Implementación de un grupo de recursos de Azure** y, luego, haga clic en el botón **Agregar** y, luego, elija **Cerrar** el **Catálogo de tareas**.

   ![Incorporación de la tarea Implementación de un grupo de recursos de Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png)
5. Elija la tarea **Copia de archivos de Azure** y rellene sus valores.

   Si ya tiene un punto de conexión de servicio de Azure agregado a Azure DevOps Services, elija la suscripción en el cuadro de lista desplegable **Suscripción de Azure**. Si no tiene suscripción, vea la [opción 1](#detailed-walkthrough-for-option-1) para obtener las instrucciones sobre cómo configurar una en Azure DevOps Services.

   * Origen: escriba **$(Build.StagingDirectory)**
   * Tipo de conexión de Azure: seleccione **Azure Resource Manager**
   * Suscripción de Azure RM: seleccione la suscripción correspondiente a la cuenta de almacenamiento que desea usar en el cuadro de lista desplegable **Suscripción de Azure**. Si la suscripción no aparece, elija el botón **Actualizar** junto al vínculo **Administrar**.
   * Tipo de destino: seleccione **Blob de Azure**
   * Cuenta de almacenamiento de RM: seleccione la cuenta de almacenamiento que desea usar para almacenar artefactos provisionalmente
   * Nombre de contenedor: escriba el nombre del contenedor que desea usar para el almacenamiento provisional; puede ser cualquier nombre de controlador válido, pero use uno dedicado a esta canalización de compilación

   Para los valores de salida:

   * URI de contenedor de almacenamiento: escriba **artifactsLocation**
   * Token SAS de contenedor de almacenamiento: escriba **artifactsLocationSasToken**

   ![Configuración de la tarea Copia de archivos de Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png)
6. Elija el paso de compilación **Implementación de un grupo de recursos de Azure** y rellene sus valores.

   * Tipo de conexión de Azure: seleccione **Azure Resource Manager**
   * Suscripción de Azure RM: seleccione la suscripción correspondiente a la implementación en el cuadro de lista desplegable **Suscripción de Azure**. Habitualmente, será la misma suscripción que se usó en el paso anterior.
   * Acción: seleccione **Creación o actualización del grupo de recursos**
   * Grupo de recursos: seleccione un grupo de recursos o escriba el nombre de un grupo de recursos nuevo para la implementación
   * Ubicación: seleccione la ubicación del grupo de recursos
   * Plantilla: escriba la ruta de acceso y el nombre de la plantilla que se implementarán; para ello, anteponga **$(Build.StagingDirectory)**, por ejemplo: **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * Parámetros de plantilla: escriba la ruta de acceso y el nombre de los parámetros que se usarán; para ello, anteponga **$(Build.StagingDirectory)**, por ejemplo: **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * Reemplazar parámetros de plantilla: escriba o copie y pegue el siguiente código:

     ```
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```

     ![Configuración de la tarea Implementación de un grupo de recursos de Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png)
7. Cuando haya agregado todos los elementos requeridos, guarde la canalización de compilación y elija **Poner nueva compilación en cola** en la parte superior.

## <a name="next-steps"></a>Pasos siguientes

Lea [Información general del Administrador de recursos de Azure](/azure/azure-resource-manager/resource-group-overview) para obtener más información sobre el Administrador de recursos de Azure y los Grupos de recursos de Azure.
