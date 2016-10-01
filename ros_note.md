

1. remap 

    when u program subscribe a topic name A, but in the ros world, only have a topic name B , and you don't want to change your code.
    you can just use this command in your launch file.
    
    eg:
    <remap from="your_program_sub_topic_name" to="ros_word_topic_has_pubished" />
    
    
    
1. rosbag record
   rosbag play
