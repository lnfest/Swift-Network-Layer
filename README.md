# Simplest network layer for swift 

## Usage

```
    func login(form: LoginForm) {
        do {
            let body = try JSONEncoder().encode(form)
            DispatchQueue.main.async {
                APIService.post(route: .login, additionalRoute: nil, body: body) { (data, response, error) in
                    DispatchQueue.main.async {
                        if let httpResponse = response as? HTTPURLResponse, let data = data  {
                            print(httpResponse)
                            switch httpResponse.statusCode {
                            case 200:
                                // decode your data
                            default:
                                // do something
                            }
                        } else {
                            // handle unexpected error
                        }
                    }
                }
            }
        } catch let error {
            // handle unexpected error
        }
    }
```



