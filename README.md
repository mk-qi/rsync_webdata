##rsync_webdata
用来同步返利网的php代码到每台服务器

基本架构
  
      normal webserver but not server user                 
     soucecode    soucecode   soucecode
         s1          s2         s3
           \         |         /
            \        |        /
             \       |       /
              \ ssh  |ssh   /ssh
               \     |     /
                lvs-cluster
                  /  |   \
                 /   |    \
                /    |     \
              rsync  |rsync \rsync over ssh
              /      |       \
             /       |        \
        phpweb1    phpweb2   phpweb..              
           \         |         /
             \       |       /             
               \     |     /
                 \   |   /   
               ssh or crontab
                     |
                     |        / call rsync pull code
                 rsync_webdata
                              \ trigger call rsync