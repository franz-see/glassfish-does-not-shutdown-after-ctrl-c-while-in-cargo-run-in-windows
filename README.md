How to recreate issue
=============

1. Checkout this code in a Windows 7 environment
2. Create the war (mvn clean package; see sample log in https://raw.github.com/franz-see/glassfish-does-not-shutdown-after-ctrl-c-while-in-cargo-run-in-windows/master/build_mvn_cargo_run_X_P_glassfish3x.log)
3. Run the war with glassfish profile (mvn cargo:run -X -Pglassfish3x; see sample log in https://raw.github.com/franz-see/glassfish-does-not-shutdown-after-ctrl-c-while-in-cargo-run-in-windows/master/build_mvn_cargo_run_X_P_glassfish3x.log)
4. Once succesfully running, to to http://localhost:8080/test to verify that the application is running (you should see a 'Hello World' message)
5. Go back to command line and press Ctrl+C
6. Revisit http://localhost:8080/test to see if the application is still running. (Expected: You should get a 404 error. Actual : 'Hello World' message)
7. Re-run cargo (mvn cargo:run -X -Pglassfish3x) (Expected: application should run successfully: Actual: cargo:run fails since the previous glassfish instance is still running; see sample log in https://raw.github.com/franz-see/glassfish-does-not-shutdown-after-ctrl-c-while-in-cargo-run-in-windows/master/build_mvn_cargo_run_X_P_glassfish3x_2nd_run.log)