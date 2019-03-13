# rabbitmq-cluster-in-k8s

       rabbitmq Cluster��kubernetes�в����ǻ���rabbitmq��Cluster Formation and Peer Discovery���ƣ����нڵ���Զ����֣��ǳ�����ʵ�ּ�Ⱥ�ĺ�����չ��ʵ��Cluster Formation and Peer Discovery��ͨ������rabbitmq-peer-discovery-k8s���ʵ�ֵġ��˲��������rabbitmq 3.7���ϰ汾��3.6�汾���Բο�autocluster�������������õĹٷ���rabbitmq:3.7.4����
       1������serviceAccount
        kubectl create -f  rbac.yml

       2������rabbitmq�������ļ�
       �����ļ�����rabbitmq.conf��enabled_plugins������rabbitmq.confΪ�������ļ���enabled_plugins��rabbitmq���õĲ����
       ����rabbitmq.conf�в��ֲ�������peer discovery��

       cluster_formation.k8s.address_type = ip
       cluster_formation.node_cleanup.only_log_warning = false
       cluster_formation.node_cleanup.interval = 30
       cluster_partition_handling = autoheal
       loopback_users.guest = false

       3������statefulset��Դ
       4������service
      ����NodePort��¶web����˿�15672��ҵ��˿�5672�����Ը���ʵ�����󣬲���ingress���ж˿ڵı�¶��
      
       5����Ⱥ��չ
       ��Ⱥ��չͨ��kubectl scale��չ���ɡ�
       kubectl scale statefulset rabbitmq --replicas=num