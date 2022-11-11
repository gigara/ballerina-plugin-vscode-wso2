# Try graphql services with Ballerina
GraphQL is an open-source data query and manipulation language for APIs. While you develop a HTTP service you need to try it and debug how it works. Ballerina VSCode plugin provide the graphqk try it view which gives the ability to try graphql services within VSCode instead of using any thrid party software.

## Set up the prerequisites
1. Install the latest versions of [Ballerina](https://ballerina.io/downloads/) and [Ballerina Visual Studio Code plugin](https://marketplace.visualstudio.com/items?itemName=wso2.ballerina).

2. Execute the command below to create a package (if you are not already working on one).

    ```bash
    bal new convert
    ```
3. Open the created package in VS Code.

## Write graphql service
1. Add the code below to the main.bal file
    ```ballerina
    import ballerina/graphql;
    
    # A service representing a network-accessible GraphQL API
    service / on new graphql:Listener(8090) {
    
        # A resource for generating greetings
        # + name - the input string name
        # + return - string name with greeting message or error
        resource function get greeting(string name) returns string|error {
            // Send a response back to the caller.
            if name is "" {
                return error("name should not be empty!");
            }
            return "Hello, " + name;
        }
    }
    ```
    Once you add the above function, the VS Code plugin will display a code lens called ` Try it ` on top of the function.
    
2. Click the Design ` Run ` code lens to run the program. This will open the terminal and start running service.
3. Click the Design ` Try it ` code lens to open the graphql try it view.
 >**Info:** The service must be in running state to use the graphql try it view
4. Once the graphql view is opened, click ` Explorer ` button to open the explorer view. You can find availble APIs from the side menu opened. 
5. Select the API/s from the explorer menu to try. This will automatically generate the payload in editor. You can edit the payload and add the required parameters (Ex: Type you name under the name parameter). ` Pretify ` button will format the code for you.
6. Click ` Run ` button to send the request. The response will be displayed in the right side window.

  ![Graphql try it](./../../resources/release-notes/3.3.0/graphql-tryit.gif)