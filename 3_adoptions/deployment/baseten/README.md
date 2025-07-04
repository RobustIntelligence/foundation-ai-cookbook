# Deployment and Inference with Baseten

[Baseten](https://www.baseten.co/) can be used to deploy the base model for inference. <br>
Sample code bundles are provided for deployment on the platform. <br>
Please note that we assume you already have Baseten accounts or contracts and are aware that deployments will incur costs.

## Deploy the model
1. Install Truss:
```bash
pip install --upgrade truss
```
2. Copy the foundation_sec_8b folder to the current directory.
3. Deploy the model:
```bash
truss push # You would be prompted to provide API key. If you don't have one, you can get it from the console.
```
4. Run Inference
Once it's deployed, you can run inference using the endpoint.
```python
import requests

ENDPOINT_URL = "" # Replace with your endpoint URL
API_KEY = "" # Replace with your API key

def inference(prompt):
    data = {'prompt': prompt}
    # If you want to add your own generation_args, you can do so like this:
    # data['generate_args'] = YOUR_GENERATION_ARGS
    response = requests.post(
        ENDPOINT_URL,
        headers={"Authorization": f"Api-Key {API_KEY}"},
        json=data,
    )
    return response.text
```
`YOUR_GENERATION_ARGS` is a dictionary containing generation arguments. <br>
For more details, refer to the [configuration section of quickstart guide](https://github.com/RobustIntelligence/foundation-ai-cookbook/blob/main/1_quickstarts/Quickstart_Foundation-Sec-8B.ipynb).
