



 Lisaülesanne: Navigeerimise sihtmärgid koodis
===============================================











> 
> 
> **Eelmises harjutuses kasutasime autonoomse navigeerimise sihtmärgi seadmiseks RVizis olevat 2D Nav Goal nuppu. Arendajal võib aga tekkida soov saata robotile navigeerimiskäsk koodis, et siis pärast roboti õigesse kohta jõudmist saaks tal lasta sooritada mõnd muud vajalikku tegevust. Siin harjutuses vaatame, kuidas anda robotile sihtpunkt ette Pythoni koodis.**
> 
> 
> 
> 



 Käivita kõik kimbud ja sõlmed simulatsioonis navigeerimise jaoks samamoodi, nagu eelmises harjutuses. Soovi korral võid küll RVizi visualiseerimise käivitamata jätta ja vaadata vaid Gazebo akent.




 Siis loo endale sobiva kimbu scripts-kausta uus koodifail, mille sisu leiad altpoolt. Märgi see käivitatavaks failiks, kompileeri catkini tööruum ja laadi see. Lõpuks käivita äsjaloodud sõlm.




```
#!/usr/bin/env python3
import rospy
import actionlib
from move_base_msgs.msg import MoveBaseAction, MoveBaseGoal

def send_goal_client():
    
    client = actionlib.SimpleActionClient('move_base',MoveBaseAction)
    client.wait_for_server()

    goal = MoveBaseGoal()
    x = [0.2, 2.2]
    y = [1.0, 2.0]
    goal.target_pose.header.frame_id = "map"
    goal.target_pose.header.stamp = rospy.Time.now()
    goal.target_pose.pose.position.x = x[k]
    goal.target_pose.pose.position.y = y[k]
    goal.target_pose.pose.orientation.w = 1.0

    client.send_goal(goal)
    wait = client.wait_for_result()
    if not wait:
        rospy.logerr("Action server not available!")
        rospy.signal_shutdown("Action server not available!")
    else:
        return client.get_result()

if __name__ == '__main__':
    global k
    try:
        rospy.init_node('send_goal')
        k = 0
        result_1 = send_goal_client()
        if result_1:
            rospy.loginfo("Goal 1 reached!")
            k += 1
        result_2 = send_goal_client()
        if result_2:
            rospy.loginfo("Goal 2 reached!")
    except rospy.ROSInterruptException:
        rospy.loginfo("Navigation finished.")
```


 See sõlm suunab roboti kahte erinevasse sihtpunkti: koordinaatidel (0,2; 1,0) ja (2,2; 2,0). Seejärel lõpetab ta töö.




 Võid koodi sisu endale sobival viisil muuta ja sellega mängida. Kui soovid, võid katsetada ka päris robotil - siis on kindlasti vaja teistsuguseid sihtmärgikoordinaate.



 







