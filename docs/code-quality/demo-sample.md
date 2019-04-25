---
title: Proyecto de ejemplo de C++ para el análisis de código
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ad28cae5e548a35e0166e1d8ed451450264241f7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943511"
---
# <a name="sample-c-project-for-code-analysis"></a>Proyecto de ejemplo de C++ para el análisis de código

El procedimiento siguiente muestra cómo crear el ejemplo de [Tutorial: Analizar código de C/C++ en busca de defectos](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). El procedimiento crea:

- Una solución de Visual Studio denominada CppDemo.

- Un proyecto de biblioteca estática denominado CodeDefects.

- Un proyecto de biblioteca estática denominado Annotations.

Los procedimientos también proporcionan el código para el encabezado y los archivos *.cpp* para las bibliotecas estáticas.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Crear la solución CppDemo y el proyecto CodeDefects

1. Haga clic en el menú **Archivo**, seleccione **Nuevo** y haga clic en **Nuevo proyecto**.

2. En la lista de árbol **Tipos de proyecto**, si Visual C++ no es el lenguaje predeterminado en VS, expanda **Otros lenguajes**.

3. Expanda **Visual C++** y luego haga clic en **General**.

4. En **Plantillas**, haga clic en **Proyecto vacío**.

5. En el cuadro de texto **Nombre**, escriba **CodeDefects**.

6. Active la casilla **Crear directorio para la solución**.

7. En el cuadro de texto **Nombre de la solución**, escriba **CppDemo**.

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurar el proyecto CodeDefects como una biblioteca estática

1. En Explorador de soluciones, haga clic con el botón derecho en **CodeDefects** y luego haga clic en **Propiedades**.

2. Expanda **Propiedades de configuración** y haga clic en **General**.

3. En la lista **General**, seleccione el texto de la columna situada junto a **Extensión de destino** y escriba **.lib**.

4. En **Valores predeterminados del proyecto** , haga clic en la columna situada junto a **Tipo de configuración** y luego haga clic en **Biblioteca estática (.lib)**.

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Agregar el archivo de encabezado y código fuente al proyecto CodeDefects

1. En Explorador de soluciones, expanda **CodeDefects**, haga clic con el botón derecho en **Archivos de encabezado**, haga clic en **Agregar** y luego en **Nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Código** y luego en **Archivo de encabezado (.h)**.

3. En el cuadro **Nombre**, escriba **Bug.h** y haga clic en **Agregar**.

4. Copie el código siguiente y péguelo en el archivo *Bug.h* en el editor de Visual Studio.

    ```cpp
    #include <windows.h>

    //
    //These 3 functions are consumed by the sample
    //  but are not defined. This project cannot be linked!
    //

    bool CheckDomain( LPCSTR );
    HRESULT ReadUserAccount();

    //
    //These constants define the common sizes of the
    //  user account information throughout the program
    //

    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

5. En Explorador de soluciones, haga clic con el botón derecho en **Archivos de código fuente**, seleccione **Nuevo** y haga clic en **Nuevo elemento**.

6. En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Archivo C++ (.cpp)**.

7. En el cuadro **Nombre**, escriba **Bug.cpp** y haga clic en **Agregar**.

8. Copie el código siguiente y péguelo en el archivo *Bug.cpp* en el editor de Visual Studio.

    ```cpp
    #include <stdlib.h>
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount() )
        {

            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )
            {
                if ( g_userAccount[len] == '\\' )
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete [] domain;
                return false;
            }
            else
            {
                domain[len]='\0';
            }
            // Process domain string
            bool result = CheckDomain( domain );

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i+j;
    }
    ```

9. Haga clic en el menú **Archivo** y luego en **Guardar todo**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Agregar el proyecto Annotations y configurarlo como una biblioteca estática

1. En Explorador de soluciones, haga clic en **CppDemo**, seleccione **Agregar** y haga clic en **Nuevo proyecto**.

2. En el cuadro de diálogo **Agregar nuevo proyecto**, expanda Visual C++, haga clic en **General** y luego en **Proyecto vacío**.

3. En el cuadro de texto **Nombre**, escriba **Annotations** y haga clic en **Agregar**.

4. En Explorador de soluciones, haga clic con el botón derecho en **Annotations** y luego haga clic en **Propiedades**.

5. Expanda **Propiedades de configuración** y haga clic en **General**.

6. En la lista **General**, seleccione el texto de la columna situada junto a **Extensión de destino** y escriba **.lib**.

7. En **Valores predeterminados del proyecto** , haga clic en la columna situada junto a **Tipo de configuración** y luego haga clic en **Biblioteca estática (.lib)**.

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Agregar el archivo de encabezado y código fuente al proyecto Annotations

1. En Explorador de soluciones, expanda **Annotations**, haga clic con el botón derecho en **Archivos de encabezado**, haga clic en **Agregar** y luego en **Nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Archivo de encabezado (.h)**.

3. En el cuadro **Nombre**, escriba **annotations.h** y haga clic en **Agregar**.

4. Copie el código siguiente y péguelo en el archivo *annotations.h* en el editor de Visual Studio.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();

    ```

5. En Explorador de soluciones, haga clic con el botón derecho en **Archivos de código fuente**, seleccione **Nuevo** y haga clic en **Nuevo elemento**.

6. En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Código** y luego en **Archivo C++ (.cpp)**.

7. En el cuadro **Nombre**, escriba **annotations.cpp** y haga clic en **Agregar**.

8. Copie el código siguiente y péguelo en el archivo *annotations.cpp* en el editor de Visual Studio.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>
    #include <windows.h>
    #include <stdlib.h>
    #include "annotations.h"

    LinkedList* AddTail( LinkedList *node, int value )
    {
        LinkedList *newNode = NULL;

        // finds the last node
        while ( node->next != NULL )
        {
            node = node->next;
        }

        // appends the new node
        newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }

    ```

9. Haga clic en el menú **Archivo** y luego en **Guardar todo**.
