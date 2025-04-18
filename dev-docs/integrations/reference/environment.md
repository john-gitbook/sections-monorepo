# Environment

GitBook defines the environment your integration runs in. It's a contextual object and includes information about the space your integration is installed in, custom environment variables, and more.

You can access this information in your integration by parsing the `environment` argument passed in the `render()` and `fetch()` methods when creating your [components](createcomponent.md) and [integrations](createintegration.md).

### Integration Environment

This is the main object exposed to your integration, and can be found by calling the `context.environment` object.&#x20;

When reading information about your integration, you should default to using `spaceInstallation` information.

<pre class="language-typescript"><code class="lang-typescript">environment: {
    /** URL of the HTTP API */
    apiEndpoint: string;
    
    /** Authentication token to use with the HTTP API */
    apiTokens?: {
        properties: {
            /** Authentication token representing the integration */
            integration: string;
            /** Authentication token representing the installation */
            installation:string;
        }
    };
    
    /** Information about the integration */
    integration: Integration;
    
    /** Installation of an integration at a site level */
    siteInstallation?: {
        /** ID of the space the integration is installed on. */
        space: string;
        
        status: {
            Active = "active",
            Pending = "pending",
            Paused = "paused"
        };
        
        /** 
        Custom configuration variables of the integration at a space level. 
        See the Configurations section to learn more.
        */
        configuration: {};
        
        externalIds: any;
        
        /** URLs associated with the object */
        urls: {
            publicEndpoint: string;
        };
    };
    
    /** Installation of an integration on an organization */
    installation?: {
        id: string;
        
        status: {
            Active = "active",
            Pending = "pending",
            Paused = "paused"
        };
        
        /** 
        Describe whether all spaces have been selected 
        or there's a selection involved 
        */
        space_selection: {
            All = "all",
            Selected = "selected"
        };
        
        /** 
        Custom configuration variables of the integration at the organization level. 
        See the Configurations section to learn more.
        */
        configuration: {};
        
        /** URLs associated with the object */
        urls: {
            app: string;
            publicEndpoint: string;
        };
        
        /** External IDs assigned by the integration. */
        externalIds: string[];
        
        /** Target of the integration installation */
        target: IntegrationInstallationTarget;
    };
<strong>    
</strong>    /** Secrets stored on the integration and passed at runtime. */
    secrets: IntegrationSecrets;
}
</code></pre>
