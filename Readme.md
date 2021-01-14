    kubectl apply mattermost.yaml -n staging
    kubectl apply mattermost.yaml -n preprod

###### https://github.com/mattermost/mattermost-docker/blob/master/contrib/kubernetes/README.md

Problem with postgres:9, use latest..

    echo -n "password" | base64 -d --> Postgres error if no "-n"
    {"level":"error","ts":1610654342.6151483,"caller":"sqlstore/supplier.go:252","msg":"Failed to ping DB","error":"parse \"postgres://mattermost\\n:azertyuiop%0A@postgres:5432/mattermost\\n?sslmode=disable&connect_timeout=10\": net/url: invalid control character in URL","retrying in seconds":10}


Debug dns:

    kubectl apply -f https://k8s.io/examples/admin/dns/dnsutils.yaml



===> config map KO

    ~/workspace$ kubectl logs mattermost-5d5db95b8-bfcj5
    No configuration file /mattermost/config/config.json
    Creating a new one
    Configure database connection...
    OK
    Starting mattermost
    {"level":"error","ts":1610655627.5247104,"caller":"app/server.go:439","msg":"Mail server connection test is failed: SendEmailNotifications is not true"}
    {"level":"error","ts":1610655627.5247478,"caller":"app/server.go:443","msg":"SiteURL must be set. Some features will operate incorrectly if the SiteURL is not set. See documentation for details: http://about.mattermost.com/default-site-url"}


ping postgres ne réagit pas !!!
ping mattermost OUI



Charts Helm !! https://github.com/mattermost/mattermost-helm




    default       mattermost-5d4769795f-rpqhv        0/1     CrashLoopBackOff   2          62s
    default       mattermost-5d4769795f-z2vsl        0/1     CrashLoopBackOff   2          43s

--> Error: failed to load configuration: unable to load on store creation: failed to persist: failed to write file: open /mattermost/config/config.json: read-only file system
https://github.com/mattermost/mattermost-helm/issues/100

