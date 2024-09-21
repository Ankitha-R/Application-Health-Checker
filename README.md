import requests

def check_application_health(url):
    try:
        # Send an HTTP GET request to the application URL
        response = requests.get(url, timeout=5)
        
        # Check if the response status code indicates a healthy application
        if response.status_code == 200:
            print(f"Application is UP. Status Code: {response.status_code}")
        else:
            print(f"Application is DOWN. Status Code: {response.status_code}")
    
    except requests.exceptions.Timeout:
        print("Error: Application is DOWN. Request timed out.")
    
    except requests.exceptions.ConnectionError:
        print("Error: Application is DOWN. Unable to connect to the server.")
    
    except Exception as e:
        print(f"An unexpected error occurred: {e}")

# Example usage
if __name__ == "__main__":
    url = "http://example.com"  # Replace with your application's URL
    check_application_health(url)
