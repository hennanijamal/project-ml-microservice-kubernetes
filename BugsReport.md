**BUG**:

- OSError: [Errno 8] Exec format error: '/app/app.py'
- AttributeError: 'LeastSquaresError' object has no attribute 'get_init_raw_predictions'

**FIX**

- upgrade to python3.7
- add werkzeug==0.14.1 to requirements.txt
- uses sci-kit learn version 0.20.3

***Note!***

I made some few modifications to the original helper code before I could successfully run the poject
- I added the some dependences to the `requirements.txt` file: `joblib` and `werkzug==0.14.1`. 
- I also downgrade `scikit-learn` to `scikit-learn==0.20.3`.
- I also had to use the appropirate indentations of the text on the comfig.yml file.

### Referernce

- https://stackoverflow.com/questions/55320496/oserror-errno-8-exec-format-error-python
- https://hackernoon.com/publish-your-docker-image-to-docker-hub-10b826793faf
- https://www.udacity.com/course/scalable-microservices-with-kubernetes--ud615
- https://hackernoon.com/publish-your-docker-image-to-docker-hub-10b826793faf