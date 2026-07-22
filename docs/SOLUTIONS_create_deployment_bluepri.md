# Function to establish secure deployment context 
def initialize_deployment_context(managed_identity_client):
    """
    Establishes the execution context using a Managed Identity 
    associated with the Blueprint Assignment resource.
    """
    try:
        # Assumes pre-configured role assignment on the target scope (Resource Group/Subscription)
        credential = managed_identity_client.get_credentials()
        print(f"✅ Context established for ID: {credential['id']}")
        return credential
    except Exception as e:
        raise SecurityError("Failed to acquire necessary Managed Identity context.") 

# Execution point for the main deployment routine
# security_context = initialize_deployment_context(...) 