# Model Aggregator App

This app, together with the `model_local_training_app`, form a semi-FL app using SyftBox

## Running in dev mode

0. Run 3 clients (`a, b, c`) with `just run-client a` and the SyftBox cache server `just run-server`
1. Install the local training app on `b, c`: `syftbox app install https://github.com/OpenMined/model_local_training --config_path <path_to_config.json>` where `<path_to_config.json>` points to `b` or `c`'s `config.json` file
2. Install the model aggregator app on `a`: `syftbox app install https://github.com/OpenMined/model_aggregator --config_path <path_to_config.json>` where `<path_to_config.json>` points to `a`'s `config.json` file
3. Copy the `participants.json` into `a`'s `api_data/model_aggregator/launch` folder, e.g. `.clients/a@openmined.org/datasites/a@openmined.org/api_data/model_aggregator/launch/participants.json`. 
4. Copy the test data, e.g. `mnist_dataset.pt` into .`clients/a@openmined.org/private/model_aggregator/`
5. Moving the MNIST data parts in `b` and `c`'s `private` into `private/model_local_training` to train
5. The training logs can be seen at the `apis/model_aggregator/logs` folder for `a`, or `apis/model_local_training/logs` for `b` and `c`