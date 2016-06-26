#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

# Start from a Java image.
FROM java:7

# Ignite version
ENV GRIDGAIN_VERSION 7.5.11

WORKDIR /opt/gridgain

#http://gridgain.com/media/

ADD ./gridgain-enterprise-fabric-$GRIDGAIN_VERSION.zip /opt/gridgain/gridgain-enterprise.zip

# Ignite home
ENV IGNITE_HOME /opt/gridgain/gridgain-enterprise-fabric-$GRIDGAIN_VERSION

RUN unzip gridgain-enterprise.zip

RUN rm gridgain-enterprise.zip

ADD https://github.com/kemiz/IgnitePrimedCacheExample/archive/master.zip IgnitePrimedCacheExample-master.zip

RUN unzip IgnitePrimedCacheExample-master.zip

RUN rm IgnitePrimedCacheExample-master.zip

ADD ./data.zip 0_0.zip

RUN unzip 0_0.zip

RUN rm 0_0.zip

RUN mkdir -p /opt/gridgain/default/0_0_0_0_0_0_0_1_1_127_0_0_1_172_17_0_1_172_18_0_1_192_168_65_2_47500/IgnitePrimedCacheExample-master/

RUN cp 0_0 /opt/gridgain/default/0_0_0_0_0_0_0_1_1_127_0_0_1_172_17_0_1_172_18_0_1_192_168_65_2_47500/IgnitePrimedCacheExample-master/

RUN apt-get update

RUN apt-get install -y maven

RUN mvn -f IgnitePrimedCacheExample-master/pom.xml package

# Copy sh files and set permission
ADD ./run.sh $IGNITE_HOME/

RUN chmod +x $IGNITE_HOME/run.sh

CMD $IGNITE_HOME/run.sh

EXPOSE 11211 47100 47500 49112
